# Your AI Agents Need an Audit Committee

---

On March 9, 2026, CodeWall [published a writeup](https://codewall.ai/blog/how-we-hacked-mckinseys-ai-platform) about McKinsey's internal AI platform, Lilli. Their autonomous offensive agent found a SQL injection. No human in the loop. Within two hours, it had full read and write access to the production database. 46.5 million chat messages. 728,000 files. 57,000 user accounts. Decades of proprietary McKinsey research.

The agent had write access to the system prompts. The instructions that control how Lilli behaves for 43,000 consultants. An attacker could have rewritten those prompts silently. No deployment. No code change. One UPDATE statement. Lilli starts giving poisoned advice to every consultant at the firm. Nobody notices because the output comes from their own internal tool.

SQL injection has been in the OWASP Top 10 since 2003. Lilli had been in production for over two years. McKinsey has world-class technology teams. No structural check caught it. No separation between the data layer and the prompt layer. No integrity monitoring. No independent validation that the instructions governing AI behavior hadn't been tampered with.

I went from Bain to a quota-carrying AE role at Zapier. I co-run a startup where AI agents handle nearly everything. The lesson from both environments: quality is determined by the system that validates the work, not the system that produces it.

In consulting, an analyst builds the slide. A consultant checks the analysis. A manager checks the framing. A partner checks the story. The person who creates the work never evaluates it. No one is a reliable judge of their own output. Banking calls this maker-checker. Pharma calls it clinical trial blinding. Accounting calls it separation of duties. SOX compliance is built on it. The global financial system depends on the idea that the person who produces something should not be the person who validates it.

That principle is absent from how we build AI agent systems in 2026.

The most common "validation" in agent frameworks is reflection. The agent reviews its own output before returning it. It catches typos. It does not catch bad judgment. Acko Insurance figured this out and built a separate checker agent with different prompts and temperature settings. Their checker improved roughly 40% of extractions in production. They applied it to one pipeline. The question is what happens when you generalize it.

I went deep into the codebase of an open-source agent orchestration platform. Roles, reporting lines, budgets, heartbeat-based scheduling. Agents modeled as employees, tasks as issues, work flowing through a ticket system. Sophisticated. Zero automated validation that work was actually completed correctly. The agent self-reports "done." The system marks it done. Every employee writes their own performance review and it goes straight into their permanent file. No manager review. No peer feedback. No audit. We would never accept this from human organizations.

The patterns for solving this have existed for decades. They just haven't been codified for machines.

In banking, the person who creates a transaction cannot approve it. A wire transfer needs a separate pair of eyes. For agent systems, this means the agent that produces work cannot mark it complete. A different agent reviews it. In pharma, the investigator doesn't know which patients are in the control group. The evaluator structurally cannot game the results. For agents, the builder never sees the acceptance criteria. The validator has criteria the builder can't access. The builder can't optimize for the rubric because it doesn't know the rubric exists. SOX compliance requires that no single person controls an entire financial process. For agents, this means different instances, different context windows, different tool access. A prompt that says "be critical" is a policy. An agent that cannot see the builder's reasoning is a constraint. Constraints beat policies.

I built a financial model with AI agents. The balance sheet didn't balance in months 11 and 12. A simple automated check would have caught it instantly.

Most knowledge work has two layers. A financial model should balance. That's testable. It should also have defensible assumptions. That's judgment. A sales email should spell the prospect's name right. Testable. It should address their specific pain point. Judgment. Check the testable layer with scripts. Check the judgment layer with a second agent applying a rubric. Run both.

For code, we have test suites. The builder writes the code. The tests check it. The builder never sees the assertions until they fail. Solved problem. For everything else, we need holdout rubrics. Structured evaluation criteria injected into a validator agent's context but never shown to the builder. Clinical trial blinding for knowledge work.

When the validator rejects work, feedback follows tiers. Enough for the builder to fix the issue without revealing the acceptance criteria. "The balance sheet doesn't balance in the second half of the year." Not "the inventory adjustment in cell B47 wasn't reflected in equity."

In a traditional company, humans do the work, the validation, and the governance. Deep hierarchy because coordination among humans is expensive. In an AI-first company, agents do the work. Different agents do the validation. Humans do governance at the top, for judgment calls the system can't make. The human org is radically flat. One to three people with clear domains of judgment. No middle management. Agents handle coordination. The hierarchy didn't disappear. It moved to where it scales.

Not everything needs the same scrutiny. Organizing notes gets post-hoc sampling. A research summary gets a single-agent rubric check. A draft email gets multi-agent review. A financial commitment gets multi-agent review plus a human gate. A legal signature stays human-only. The system classifies risk and routes to the appropriate pipeline.

Go back to the McKinsey breach. Five structural protections would have mitigated it at different layers. Separate the prompt layer from the data layer so the system that executes prompts can't store or modify them. Monitor prompt integrity by periodically hashing system prompts against known-good versions. Run maker-checker on AI output so an attacker has to compromise both the builder and the validator. Tier validation by risk so high-stakes queries get multi-agent review while routine questions flow freely. Automate API-layer checks so "every endpoint serving production data requires authentication" runs on every release instead of going unchecked for two years.

McKinsey didn't fail because they had bad engineers. The governance layer around their AI system didn't exist as a distinct concern. Prompts were treated as configuration. The API surface was an engineering detail. AI output was trusted because it came from an internal tool. Mundane, structural, catch-it-with-a-checklist governance. Applied to AI systems with the same rigor we apply to financial reporting. The patterns have existed for 90 years. We haven't built them for machines.

Simon Willison's [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) captures the individual developer side well. One developer working with one agent. I'm interested in what happens when the agents are the organization. A team of agents producing financial models, sales emails, strategy docs. No human can review all of it. The validation problem becomes structural.

I'm building this in the open. The [validation-rubrics repo](https://github.com/a1j9o94/validation-rubrics) has the first rubric (financial models) with automated checks, judgment criteria, and pass/fail examples. Every domain needs its own. Contributions welcome.

---

*Adrian Obleton is an Account Executive at Zapier. Previously at Bain & Company. HBS '23.*

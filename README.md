# Sancak - /ˈsɑn.dʒak/ - AI-Assisted Coding Methodology & Framework

This is a structured product development methodology that leverages AI/human interaction for software development. It enforces test-driven development, hierarchical requirements, and role-based collaboration between AI agents and humans. The AI will be guided to operate within the framework using the markdown files in `/docs` so it's a good place to go to understand it yourself. 

## Design Philosophy and Features
This framework embodies specific opinions about effective software development that we believe apply equally to human and AI collaboration:
- **Requirements First, Always**  
  Code without clear, testable requirements is speculation. We enforce requirement definition before any implementation begins, with each requirement traceable through tests to code.
- **Test-Driven Development is Non-Negotiable**  
  Tests aren't documentation — they're executable specifications. Writing tests first forces clarity about what "done" means and prevents scope creep during implementation.
- **Breadth Before Depth**  
  Like story mapping, we prioritize end-to-end functionality over feature completeness. Build the MVP spine first, then add sophistication. This keeps the system functional at every milestone.
- **Role Clarity Prevents Chaos**  
  Different cognitive modes require different contexts. A technical product manager thinks differently than a developer. We enforce role boundaries to maintain focus and accountability.
- **Incremental Progress with Human Oversight**  
  AI can implement, but humans must understand and approve. One subtask at a time, with human checkpoints, prevents runaway automation and maintains code ownership.
- **Documentation is Code**  
  If it's not written down with the same rigor as code, it doesn't exist. Requirements, architectural decisions, and task status live in version control alongside implementation.
- **Scientific Problem Solving**  
  When things break, form hypotheses and test them systematically. This prevents the "try random things until it works" antipattern common in AI-assisted development.
- **Tool Agnostic by Design**  
  Good methodology shouldn't depend on specific tools. Markdown and git are universal; everything else is replaceable.

---

If these principles resonate with your approach to software development, I'm hopeful this methodology and framework will feel natural and enable productive sotware product development.

## Usage

Clone this repo as the baseline of your project, or unzip into an existing project. Then to begin using it, include the markdown files from `/docs` in your AI chatbot context, and initiate projects with a phrase like:

"Help me write the requirements for a product that..."

## Framework Files

- `/docs/PROJECT.md` - Main requirements, tests, and architectural decisions
- `/docs/ROLES.md` - Role definitions and responsibilities  
- `/docs/PROMPTS.md` - AI agent prompts for each role
- `/docs/WORKFLOW.md` - Process guidelines and state management

## About the Name: Sancak

**Sancak** means *flag*, *banner*, or *standard* in Turkish. As a project seeking to enforce the critical roles in a software project, **Sancak** acts as a standard-bearer for disciplined, collaborative development. It symbolizes the unifying principles under which architects, engineers, product managers, testers, and AI agents align — ensuring clarity, accountability, and rigorous progress at every step. Just as a banner guides and inspires those who march under it, the **Sancak** methodology provides a visible standard for building software the “right way.”

## Acknowledgments

This framework was inspired by the markdown files in ai-dev-tasks [https://github.com/snarktank/ai-dev-tasks] by snarktank, particularly their approach to using structured markdown files for AI-assisted development workflows. 

The files in this repo were created with the assistance of Anthropic/Claude. 

### License
The contents of this repo are licensed under the Creative Commons Attribution-ShareAlike 4.0 license. https://creativecommons.org/licenses/by-sa/4.0/deed.en

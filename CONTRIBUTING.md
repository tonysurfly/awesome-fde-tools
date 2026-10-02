# Contributing

An entry belongs here when it addresses a difficult, recurring customer-delivery problem. "An FDE might use it" is not enough.

## What earns inclusion

- A specific customer failure or decision, such as inconsistent record identities, revoked access, unavailable dependencies, schema drift, or retried writes.
- Working code and documentation sufficient to start using it.
- An accurate deployment and edition boundary when it affects the described capability.
- Current usefulness. A stable utility can remain useful without frequent releases.
- A meaningful distinction from tools already listed.

There is no minimum star count. A small tool that solves a recurring field problem can be more useful than a large framework.

## What to leave out

Avoid thin wrappers, abandoned demos, affiliate directories, and unsupported performance claims. General developer-stack essentials such as Docker, language frameworks, databases, diagram editors, and package managers are outside the scope. Do not add every agent framework or evaluation library. Explain why readers need another option.

Commercial and source-available tools require an explicit reason to include them. Prefer an open-source option when it meets the same need. Never describe fair-code, business-source, or restricted model weights as unrestricted open source.

## Entry format

```md
- <a href="https://github.com/owner"><img src="https://github.com/owner.png?size=48" width="20" height="20" alt="" title="owner on GitHub"></a> **[Tool](https://github.com/owner/repo)** `specific job`<br>
  The documented mechanism and the concrete customer-delivery task it helps with.<br>
  <sub>Field note: The limitation or condition that matters when choosing this tool.</sub>
```

Use the repository owner's avatar, not an unrelated product logo. Keep the description and field note on separate indented lines. For a restricted project, add a short label after its job tag:

```md
`specific job` `source-available`
```

Use one canonical link and one main category per tool. Descriptions should name a mechanism or capability, rather than claim the tool is powerful or easy. Mention a material limitation when omitting it would mislead someone making a deployment choice.

## Evidence to include in a proposal

- Canonical repository and official documentation.
- The customer-delivery problem and proposed category.
- A material deployment restriction or enterprise-only feature when relevant.
- Documentation or an example supporting the description.
- The nearest existing alternative and the reason both should remain.
- Maintenance concerns or restrictions that the maintainer should review.

## Verify the change

```sh
python3 tools/validate.py --offline
python3 -m unittest discover -s tools -p 'test_*.py'
```

To refresh the repository-health evidence, authenticate the GitHub CLI and run:

```sh
python3 tools/validate.py --refresh
```

The refresh updates `research/github-checks.json`. Review canonical names, archive flags, and any relevant metadata notes. Update the tool-count badge and the category counts when adding or removing an entry. The snapshot only checks repository metadata. It does not test deployment, certify security, or replace reading the documentation.

Keep substantive comparison decisions in [research/README.md](research/README.md). Move or remove stale entries when a better current representative serves the same purpose.

To build a temporary README preview with GitHub's renderer and Markdown CSS, run `python3 tools/preview_readme.py`. It prints a local server command and does not publish anything. Check both desktop and mobile widths after changing the layout.

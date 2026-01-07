# Constitutional Kernel for Aligned Collective Intelligence

**Version:** 0.5.0 (Development - Pre-Ratification)  
**Status:** Development Draft  
**License:** AGPL-3.0-or-later

## Overview

The **Constitutional Kernel** is the immutable foundational law for viable coordination systems. It defines the constitutional constraints that enable autonomous entities to coordinate around shared substrate viability goals while preventing both human coordination failures and AI alignment failures.

This kernel implements the theoretical framework of **Viable Systems Theory**, **Constitutional AI**, and **Thermodynamic Economics** into a machine-readable, enforceable constitution.

## What This Is

Think of this kernel as:
- **Operating System Kernel** for coordination (not compute)
- **Constitutional Law** for federated autonomous systems
- **Game Theory Equilibrium** enforced in code
- **Thermodynamic Constraint** on artificial economies

## Core Principles

### Article 0: The Viability Covenant
Every individual has an inalienable right to inhabit a viable bioregion. The system guarantees substrate (food, water, shelter, opportunity) as a fundamental right.

### Thermodynamic Foundation
```
E_net = E_industrial + E_ecosystem + E_interaction
```
No entity may accrue positive Viability Power (VP) with negative thermodynamic balance.

### Six Constitutional Gates
1. **Thermodynamic Solvency**: E_invested < E_production
2. **Cognitive Variety**: Inject dissident models
3. **Hardware Viability**: Memory < 3GB (FM-35 prevention)
4. **Evidence Sufficiency**: Weighted epistemic score ≥ 0.7
5. **Viability Power**: R_absolute ≥ 0.5 for VP accrual
6. **Human Escalation**: High-stakes → human judgment

## Repository Structure

```
constitutional-kernel/
├── cos-kernel-v0.5.0.yml          # Machine-readable constitution
├── LICENSE                         # AGPL-3.0-or-later
├── README.md                       # This file
├── CHANGELOG.md                    # Version history
├── CONTRIBUTING.md                 # How to contribute
│
├── docs/
│   ├── philosophy/                 # Philosophical foundations
│   ├── architecture/               # System architecture
│   └── implementation/             # Implementation guides
│
├── schemas/
│   ├── contract-schema.json        # CIP contract validation
│   └── evidence-tiers.json         # Article X evidence framework
│
├── tools/
│   ├── linter/                     # Constitutional linter
│   └── validator/                  # Kernel validator
│
├── examples/
│   ├── minimal-entity.yml          # Simplest compliant entity
│   ├── bioregional-dao.yml         # Bioregional implementation
│   └── federation.yml              # Multi-bioregion federation
│
└── tests/
    ├── thermodynamic/              # Article 0 test suite
    ├── functional/                 # Article I (VSM) tests
    └── epistemic/                  # Article X tests
```

## Quick Start

### Reading the Constitution

The kernel is both human-readable and machine-executable:

```bash
# View the constitution
cat cos-kernel-v0.5.0.yml

# Validate syntax
yamllint cos-kernel-v0.5.0.yml

# Run constitutional linter (requires implementation)
./tools/linter/cos-lint.py my-proposal.yml
```

### Understanding the Structure

```yaml
# Layer 0: Functional Core (Articles 0-VII, IX-X)
article_0:  # The Viability Covenant - substrate guarantees
article_1:  # Functional Architecture - VSM structure
article_2:  # Subsidiarity - local-first decision making
# ...

# Layer 1: Meta-Constitutional (Article VIII)
article_8:  # Kernel Paradigm Shift - how to replace this kernel
```

### Key Concepts

**Viability Points (VP)**: Earned coordination power
- **VP-Base**: Local substrate stewardship
- **VP-Bonus**: Global priority contribution
- **VP-Commons**: Shared knowledge/infrastructure

**Evidence Tiers** (Article X):
- Tier 1: Lab/Sensor (1.0 weight)
- Tier 2: Observational (0.7 weight)
- Tier 3: Testimonial (0.5 weight)
- Tier 4: Proxy (0.3 weight)

**Phase Transitions**:
- Phase 1 (Genesis): 0-100 entities, Tier 4 acceptable
- Phase 2 (Adolescent): 100-1,000 entities, Tier 3 required
- Phase 3 (Mature): 1,000-10,000 entities, Tier 2 required
- Phase 4 (Systemic): 10,000+ entities, Tier 1 required

## Ratification Status

**Current Status:** Development Draft (v0.5.0)

This kernel is **NOT yet ratified**. Upon ratification via Article VIII.4.4 (Initial Ratification Pathway), the version will increment to **v1.0.0** and full enforcement begins.

### Path to Ratification

1. **Trigger**: Article 0.9 Federation Viability Threshold met
2. **Challenge Period**: 30 days for any bioregion to challenge
3. **Founding Council**: 101 sortition-selected stewards
4. **Ratification Vote**: 2/3 supermajority required
5. **Activation**: Day 1 full kernel enforcement

## Implementation Status

### Completed Components
- ✅ Kernel specification (this file)
- ✅ Thermodynamic axiom formalization
- ✅ Six-gate Linter architecture
- ✅ Evidence tier framework
- ✅ VP calculation formulas

### In Progress
- 🚧 Constitutional linter implementation
- 🚧 Contract schema (Pydantic models)
- 🚧 Test suite development
- 🚧 Example implementations

### Planned
- 📋 External Verification Schedule (Annex VIII-A)
- 📋 Equilibrium Audit Linter (Annex VIII-B)
- 📋 Measurement Equivalence Tables
- 📋 Bioregional adaptation guides

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- How to propose amendments
- Evidence requirements for claims
- Philosophical red-team process
- Development workflow

**Important**: This kernel defines immutable constitutional law. All changes require either:
- **Configuration changes** via ratifyPolicy (Article I.2.1)
- **Kernel Paradigm Shift** via Article VIII (Success or Crisis pathway)

## Versioning

```
MAJOR.MINOR.PATCH

MAJOR: Kernel Paradigm Shift (Article VIII) OR initial ratification
MINOR: New constitutional article or significant amendment
PATCH: Clarifications, bug fixes, non-breaking changes
```

Current: `v0.5.0` (Development)  
Upon ratification: `v1.0.0` (Stable)

## Related Projects

- **VCS (Viable Collective Superintelligence)**: Reference implementation of this kernel
- **COS-Scaffold**: Foundational infrastructure for COS
- **CIP (Coordination Interchange Protocol)**: API specification

## Philosophy

This kernel is designed to:
1. **Preserve human agency** while enabling AI augmentation
2. **Guarantee substrate viability** as a fundamental right
3. **Prevent coordination failures** through constitutional constraints
4. **Enable double-loop learning** via Article VIII
5. **Maintain requisite variety** through forced diversity

### The Shore (Article VIII.2)

If we achieve 101 consecutive years of:
- Planetary homeostasis
- Preserved sapience
- Systemic solvency

...then a Second Founding Convention may transcend this thermodynamic paradigm and design a successor kernel.

Until then, we operate within thermodynamic constraints.

## Security

### Threat Model

This kernel defends against:
- **FM-01 to FM-26**: Human coordination failures
- **FM-27 to FM-35**: AI alignment failures
- **FM-40 to FM-41**: Legacy system integration failures

See [docs/philosophy/failure-modes.md](docs/philosophy/failure-modes.md) for complete FMEA.

### Cryptographic Guarantees

- Immutable audit logs (Merkle tree)
- Zero-knowledge proofs for Wanderer Mode (Article 0.10)
- Distributed Steward Council sortition (Article VIII.4)

## License

This work is licensed under the **GNU Affero General Public License v3.0 or later**.

Key implications:
- ✅ Free to use, study, modify, distribute
- ✅ Network copyleft: modifications to web services must be shared
- ✅ Patent grant included
- ⚠️ Modifications must use same license
- ⚠️ Source code must be made available

See [LICENSE](LICENSE) for full text.

## Citation

If you reference this kernel in academic work:

```bibtex
@software{constitutional_kernel_2025,
  title = {Constitutional Kernel for Aligned Collective Intelligence},
  author = {{Constitutional Kernel Contributors}},
  year = {2025},
  version = {0.5.0},
  license = {AGPL-3.0-or-later},
  url = {https://github.com/[your-org]/constitutional-kernel}
}
```

## Contact

- **Issues**: https://github.com/[your-org]/constitutional-kernel/issues
- **Discussions**: https://github.com/[your-org]/constitutional-kernel/discussions
- **Email**: kernel@viable-systems.org

## Acknowledgments

This kernel builds on:
- **Stafford Beer**: Viable Systems Model
- **Elinor Ostrom**: Polycentric governance
- **Howard Odum**: Ecological energetics
- **Anthropic**: Constitutional AI
- **Game Theory**: Nash equilibrium analysis

---

**Status**: Development (v0.5.0 - Pre-Ratification)  
**Last Updated**: 2026-01-05  
**Next Milestone**: Complete Annex VIII-A (External Verification Schedule)

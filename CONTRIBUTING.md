# Contributing to VCS Project

Thank you for your interest in contributing to the **Viable Collective Superintelligence (VCS) Project**! This is the reference implementation of the Constitutional Kernel enforcement layer.

## Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [Getting Started](#getting-started)
3. [Development Setup](#development-setup)
4. [Contribution Types](#contribution-types)
5. [Development Workflow](#development-workflow)
6. [Testing Requirements](#testing-requirements)
7. [Code Style Guide](#code-style-guide)
8. [Pull Request Process](#pull-request-process)
9. [Constitutional Alignment](#constitutional-alignment)

## Code of Conduct

### Core Principles

This project implements the Constitutional Kernel, which means:

- **Article 0**: System viability takes precedence
- **Article I**: All code must map to VSM functions
- **Article I.4**: All proposals pass through six constitutional gates
- **Article VII**: We acknowledge uncertainty and limitations

### Expected Behavior

- Provide evidence for performance/viability claims
- Write tests that validate constitutional constraints
- Accept rigorous code review as a feature
- Document assumptions and edge cases
- Prioritize thermodynamic efficiency

## Getting Started

### Prerequisites

```bash
# Required
- Python 3.11+
- Git
- Virtual environment tool (venv, conda, etc.)

# Recommended
- Docker (for deployment testing)
- yamllint (for kernel validation)
- Anthropic API key (for LangGraph features)
```

### Fork and Clone

```bash
# Fork on GitHub first, then:
git clone https://github.com/YOUR_USERNAME/vcs-project.git
cd vcs-project

# Add upstream remote
git remote add upstream https://github.com/[org]/vcs-project.git
```

## Development Setup

### 1. Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 2. Install Dependencies

```bash
# Core dependencies
pip install -r requirements.txt

# Development dependencies
pip install -r requirements-dev.txt

# Optional: LangGraph dependencies
pip install -r requirements-langgraph.txt
```

### 3. Configure Environment

```bash
cp .env.example .env
# Edit .env with your configuration
```

### 4. Install Pre-commit Hooks

```bash
pre-commit install
```

### 5. Verify Setup

```bash
# Run tests
pytest tests/

# Run integration test
python integration_test.py

# Should output: ✓ All systems operational
```

## Contribution Types

### 1. Bug Fixes

**Scope**: Fixes to existing functionality

**Requirements**:
- Issue reference (create one if it doesn't exist)
- Test that demonstrates the bug
- Test that validates the fix
- No breaking changes to public APIs

**Example**:
```python
# Issue #42: Gatekeeper incorrectly rejects positive E_net

def test_gatekeeper_accepts_positive_e_net():
    """Regression test for Issue #42."""
    proposal = ThermodynamicContract(
        E_net=100.0  # Positive!
    )
    gatekeeper = Gatekeeper(mode="enforce")
    result = gatekeeper.check_proposal(proposal)
    assert result.approved
```

### 2. New Features

**Scope**: New functionality implementing kernel requirements

**Requirements**:
- Maps to Constitutional Kernel article/section
- Includes constitutional validation
- Full test coverage (unit + integration)
- Documentation with examples
- Performance benchmarks (if applicable)

**Process**:
1. Open issue proposing feature
2. Reference specific kernel article
3. Provide implementation plan
4. Get maintainer approval before coding
5. Submit PR with all requirements

### 3. Performance Improvements

**Scope**: Optimizations maintaining correctness

**Requirements**:
- Benchmark showing improvement
- Evidence of thermodynamic efficiency gain
- All tests still pass
- No constitutional violations
- Documentation of trade-offs

**Example Benchmark**:
```python
import pytest

def test_linter_performance_regression():
    """Ensure linter remains under budget."""
    proposals = generate_test_proposals(n=100)
    
    with EnergyBudget(max_tokens=50000) as budget:
        for proposal in proposals:
            linter.lint_proposal(proposal)
    
    assert budget.remaining > 0, "Linter exceeded energy budget"
```

### 4. Documentation

**Scope**: Improvements to docs/, README, docstrings

**Requirements**:
- Clear and concise
- Includes examples where appropriate
- Links to relevant kernel articles
- Validates with spell checker

### 5. Constitutional Updates

**Scope**: Changes due to kernel version updates

**Requirements**:
- References kernel version change
- Updates implementation to match
- Adds/modifies tests for new constraints
- Updates documentation

**Process**:
```bash
# Update kernel submodule
git submodule update --remote cos-kernel

# Implement new kernel features
# ... code changes ...

# Update tests
# ... test changes ...

git add cos-kernel/ src/ tests/
git commit -m "feat: implement Constitutional Kernel v0.6.0

- Add Article XI enforcement
- Update Gatekeeper for new E_interaction metrics
- Add tests for intergenerational rights

Ref: constitutional-kernel@abc123"
```

## Development Workflow

### Branch Strategy

```
main (stable, deployed to production)
├── development (integration branch)
│   ├── feature/article-xi-enforcement
│   ├── feature/escrowed-vesting
│   ├── fix/gatekeeper-memory-leak
│   └── docs/api-documentation
└── hotfix/critical-security-patch
```

### Branch Naming

```bash
# Features
feature/<short-description>
feature/article-x-section-y

# Bug fixes
fix/<issue-number>-<short-description>
fix/42-gatekeeper-rejection

# Documentation
docs/<what-youre-documenting>
docs/deployment-guide

# Hotfixes (for production issues)
hotfix/<critical-issue>
```

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting (no code change)
- `refactor`: Code restructuring
- `perf`: Performance improvement
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples**:

```bash
feat(gatekeeper): add Article 0.12 adaptive measurement

Implements adaptive measurement requirements from kernel v0.5.0.
Gatekeeper now adjusts evidence tier requirements based on VP claim
magnitude and entity trust score.

Closes #123
Ref: Article 0.12.2
```

```bash
fix(linter): correct VP calculation for negative R_absolute

Gate 5 incorrectly allowed VP accrual when R_absolute < 0.5.
Added hard gate per Article I.2.3.

Fixes #156
```

## Testing Requirements

### Test Coverage Standards

- **Unit tests**: ≥80% coverage for all new code
- **Integration tests**: All critical paths
- **Constitutional tests**: All kernel constraints

### Writing Tests

#### Unit Tests

```python
# tests/unit/test_gatekeeper.py

import pytest
from src.agents.gatekeeper import Gatekeeper
from src.contracts import ThermodynamicContract

class TestGatekeeper:
    """Unit tests for Gatekeeper (Article 0 enforcement)."""
    
    def test_rejects_negative_e_net(self):
        """Gate rejects proposals with E_net < 0."""
        proposal = ThermodynamicContract(E_net=-100.0)
        gatekeeper = Gatekeeper(mode="enforce")
        result = gatekeeper.check_proposal(proposal)
        
        assert not result.approved
        assert "thermodynamically insolvent" in result.message.lower()
    
    def test_accepts_positive_e_net(self):
        """Gate accepts proposals with E_net > 0."""
        proposal = ThermodynamicContract(E_net=100.0)
        gatekeeper = Gatekeeper(mode="enforce")
        result = gatekeeper.check_proposal(proposal)
        
        assert result.approved
```

#### Integration Tests

```python
# tests/integration/test_constitutional_pipeline.py

import pytest
from src.graph.vsm_orchestration import VSMOrchestrator

@pytest.mark.integration
async def test_full_proposal_pipeline():
    """Test proposal flows through all constitutional gates."""
    orchestrator = VSMOrchestrator()
    
    proposal = create_test_proposal()
    result = await orchestrator.coordinate_proposal(proposal)
    
    # Verify all gates were checked
    assert result.gates_passed == 6
    assert result.decision in ["APPROVE", "REJECT", "ESCALATE_HUMAN"]
    
    # Verify thermodynamic constraint
    assert result.energy_consumed < proposal.energy_budget
```

#### Constitutional Tests

```python
# tests/constitutional/test_article_0_enforcement.py

import pytest
from src.agents.gatekeeper import Gatekeeper

class TestArticle0Enforcement:
    """Validate Article 0 (Viability Covenant) enforcement."""
    
    def test_section_0_8_hard_resource_limits(self):
        """Article 0.8: Memory limit enforcement (FM-35 prevention)."""
        # Attempt to allocate > 3GB
        with pytest.raises(MemoryError):
            gatekeeper = Gatekeeper()
            gatekeeper.allocate_memory(4 * 1024**3)  # 4GB
```

### Running Tests

```bash
# All tests
pytest tests/

# Specific test file
pytest tests/unit/test_gatekeeper.py

# Specific test
pytest tests/unit/test_gatekeeper.py::TestGatekeeper::test_rejects_negative_e_net

# With coverage
pytest --cov=src tests/

# Constitutional tests only
pytest -m constitutional tests/

# Integration tests only
pytest -m integration tests/
```

## Code Style Guide

### Python Style

We follow [PEP 8](https://pep8.org/) with these tools:

- **Black**: Code formatting (line length: 100)
- **Ruff**: Linting and import sorting
- **MyPy**: Static type checking

```bash
# Format code
black src/ tests/

# Lint
ruff check src/ tests/

# Type check
mypy src/
```

### Docstrings

Use Google-style docstrings:

```python
def check_proposal(
    self,
    proposal: ThermodynamicContract,
    mode: GatekeeperMode = "advise"
) -> GatekeeperResult:
    """
    Check proposal against thermodynamic constraints (Article 0).
    
    Enforces the Viability Covenant by validating:
    - E_net > 0 (thermodynamic solvency)
    - E_invested < E_production (no energy deficits)
    - Memory usage < 3GB (FM-35 prevention)
    
    Args:
        proposal: The thermodynamic contract to validate
        mode: Enforcement mode (observe, advise, enforce)
    
    Returns:
        GatekeeperResult with approval status and explanation
    
    Raises:
        ValueError: If proposal is malformed
        MemoryError: If memory limit exceeded (enforce mode only)
    
    Examples:
        >>> proposal = ThermodynamicContract(E_net=100.0)
        >>> gatekeeper = Gatekeeper(mode="enforce")
        >>> result = gatekeeper.check_proposal(proposal)
        >>> assert result.approved
    
    Constitutional References:
        - Article 0: The Viability Covenant
        - Article 0.8: Technical Enforcement
        - Article I.4.1: Thermodynamic Solvency Gate
    """
```

### Type Hints

Always use type hints:

```python
from typing import Optional, List, Dict, Any
from src.contracts import BaseContract

def process_contracts(
    contracts: List[BaseContract],
    filters: Optional[Dict[str, Any]] = None
) -> List[BaseContract]:
    """Process and filter contracts."""
    if filters is None:
        filters = {}
    
    return [c for c in contracts if meets_criteria(c, filters)]
```

### Configuration

Pydantic for configuration:

```python
from pydantic import BaseModel, Field
from pydantic_settings import BaseSettings

class GatekeeperConfig(BaseSettings):
    """Gatekeeper configuration (Article 0)."""
    
    mode: GatekeeperMode = Field(
        default="advise",
        description="Enforcement mode"
    )
    
    memory_limit_gb: float = Field(
        default=3.0,
        ge=0,
        le=10.0,
        description="Memory limit per Article 0.8"
    )
    
    class Config:
        env_prefix = "GATEKEEPER_"
        case_sensitive = False
```

## Pull Request Process

### Before Submitting

- [ ] All tests pass locally
- [ ] Code is formatted (black)
- [ ] Code is linted (ruff)
- [ ] Type checks pass (mypy)
- [ ] Documentation is updated
- [ ] CHANGELOG.md is updated (if applicable)
- [ ] Constitutional alignment is verified

### PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix (non-breaking change fixing an issue)
- [ ] New feature (non-breaking change adding functionality)
- [ ] Breaking change (fix or feature causing existing functionality to change)
- [ ] Documentation update
- [ ] Constitutional update (kernel version change)

## Constitutional Alignment
**Maps to**: Article X, Section Y.Z
**Prevents**: FM-XX (failure mode description)
**VSM Function**: Function A/B/C/D/E

## Testing
**Test Coverage**: XX%
**New Tests**: 
- test_name_1
- test_name_2

**Manual Testing**:
- [ ] Tested with observe mode
- [ ] Tested with advise mode
- [ ] Tested with enforce mode

## Evidence
**Performance Benchmarks**:
- Before: XXX ms
- After: YYY ms
- Improvement: ZZ%

**Energy Budget**:
- Tokens consumed: XXX
- Memory used: YY MB

## Checklist
- [ ] Code follows style guide
- [ ] Self-review completed
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests pass
- [ ] No new warnings
- [ ] Constitutional constraints validated

## Related Issues
Closes #XX
Ref #YY
```

### Review Process

1. **Automated Checks**: CI/CD must pass
2. **Code Review**: At least 1 maintainer approval
3. **Constitutional Review**: Verify kernel alignment
4. **Testing**: All tests must pass
5. **Documentation**: Must be complete
6. **Merge**: Squash and merge to development

### After Merge

- Branch is deleted automatically
- Issue is closed automatically
- Changelog is updated (if needed)
- Documentation site rebuilds

## Constitutional Alignment

### Mapping to Kernel Articles

All code must map to Constitutional Kernel articles:

```python
# src/agents/gatekeeper.py

"""
Gatekeeper Agent - Article 0 Enforcement.

Constitutional Alignment:
    - Article 0: The Viability Covenant (primary)
    - Article 0.8: Technical Enforcement
    - Article I.4.1: Thermodynamic Solvency Gate

Failure Modes Prevented:
    - FM-35: Resource exhaustion
    - FM-01: Coordination failure via energy deficit

VSM Function: Function C (Homeostatic Regulation & Audit)
"""
```

### Failure Mode Prevention

Every component must document which failure modes it prevents:

| Code | Description | Prevention Mechanism |
|------|-------------|---------------------|
| FM-35 | Resource exhaustion | Hard 3GB memory limit |
| FM-01 | Energy deficit | E_net > 0 gate |
| FM-29 | Pseudo-alignment | Human escalation gate |

### VSM Function Mapping

Map code to Viable Systems Model functions:

- **Function A**: Operational execution (agents/*)
- **Function B**: Harmonization (graph/coordination.py)
- **Function C**: Audit (agents/gatekeeper.py, linters/*)
- **Function D**: Strategic adaptation (agents/strategist.py)
- **Function E**: Normative steering (Reserved for human judgment)

## Questions?

- **Issues**: https://github.com/[org]/vcs-project/issues
- **Discussions**: https://github.com/[org]/vcs-project/discussions
- **Email**: vcs@viable-systems.org

---

**Remember**: This implementation enforces constitutional law. All changes must maintain alignment with the Constitutional Kernel. When in doubt, consult the kernel documentation.

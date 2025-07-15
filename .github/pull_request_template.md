## Summary
- Bullet point describing key implementation details
- Bullet point describing architectural changes
- Bullet point describing new features or improvements

## Test plan
- [ ] All tests pass (specify count: X/X tests passing)
- [ ] Specific functionality verification
- [ ] Build verification
- [ ] Integration test verification
- [ ] Any other relevant verification steps

**Key Changes:**
- Highlight of major implementation details
- Important architectural decisions
- New patterns or approaches introduced

**Verification:**
```bash
dotnet build    # ✅ Expected status
dotnet test     # ✅ Expected status
```

Closes #[issue-number]

---

### PR Requirements
- Use bullet points in Summary section for key changes
- Include comprehensive Test plan with checkboxes (use [x] for completed items)
- Highlight Key Changes that reviewers should focus on
- Include Verification section with build/test commands and status
- Always link to the original issue with "Closes #[issue-number]"
- Follow the exact markdown structure shown above
- NEVER add any extra content such as "Generated with Claude Code", author information, or any other additions beyond the specified format
# Drift Detection Checklist

## Architecture Alignment

- [ ] Technology stack in architecture matches package.json / requirements.txt / go.mod
- [ ] Directory structure matches architecture document's module/component structure
- [ ] API endpoints match architecture API design section
- [ ] Database schema / models match architecture data model section
- [ ] Authentication / authorization implementation matches architecture security design
- [ ] Third-party integrations match architecture integration specifications
- [ ] Deployment configuration matches architecture deployment section
- [ ] Environment variables match architecture configuration requirements

## Requirements Alignment

- [ ] All functional requirements in PRD have corresponding implementation
- [ ] Non-functional requirements (performance, security, accessibility) are met
- [ ] User journeys described in PRD are implemented end-to-end
- [ ] No orphaned code exists without spec backing (features not in any requirement)
- [ ] Error handling matches PRD error scenarios
- [ ] Data validation matches PRD data constraints

## Epic/Story Alignment

- [ ] All stories marked as "done" in sprint status have complete implementations
- [ ] Acceptance criteria for completed stories are verifiable in code
- [ ] No implemented features exist without a corresponding story
- [ ] Story descriptions still accurately describe what was built
- [ ] Dependencies between stories are properly reflected in implementation order

## UX Alignment (if UI project)

- [ ] UI components match UX design wireframes
- [ ] Navigation flows match UX interaction specifications
- [ ] Form validations match UX design specifications
- [ ] Responsive behavior matches UX breakpoint definitions
- [ ] Accessibility features match UX accessibility requirements

## Documentation Alignment

- [ ] README reflects current project state
- [ ] API documentation matches actual endpoints
- [ ] Environment setup instructions are current
- [ ] Test documentation matches actual test structure

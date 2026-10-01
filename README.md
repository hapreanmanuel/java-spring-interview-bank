# Java & Spring Boot Interview Question Bank

A comprehensive, open-source question bank for software developers preparing for Java and Spring Boot interviews at leading tech companies.

![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)
![Stars](https://img.shields.io/github/stars/hapreanmanuel/java-spring-interview-bank?style=flat-square)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)

## 🎯 Features

- **500+ Curated Questions** organized by topic, difficulty, and company
- **Tested Code Examples** — Every answer includes practical, runnable code
- **Progressive Difficulty** — Easy → Medium → Hard → Staff-level
- **Real Interview Scenarios** — Based on actual interviews from FAANG and other top companies
- **Explicit Citations** — Every question traces to authoritative sources
- **Completely Free** — MIT Licensed, open-source, no ads, no paywalls
- **Easy Navigation** — Well-organized by topic with cross-references
- **Actively Maintained** — Regular updates for new Java/Spring versions

## 📚 Table of Contents

- [01 - Core Java Fundamentals](./01-core-java/)
- [02 - Spring Framework Core](./02-spring-framework/)
- [03 - Spring Boot](./03-spring-boot/)
- [04 - Data Persistence & JPA/Hibernate](./04-data-persistence/)
- [05 - REST API Design](./05-rest-apis/)
- [06 - Spring Security](./06-security/)
- [07 - Microservices Architecture](./07-microservices/)
- [08 - Testing Strategies](./08-testing/)
- [09 - Performance Tuning & JVM](./09-performance/)
- [10 - System Design & Scalability](./10-system-design/)
- [11 - Behavioral & Soft Skills](./11-behavioral/)
- [12 - Cheat Sheets & Quick Reference](./12-cheat-sheets/)

## 🚀 Quick Start

### For Interview Prep

1. **Beginners**: Start with **Easy** questions in each section
2. **Mid-Level**: Move to **Medium** questions after mastering basics
3. **Senior Prep**: Focus on **Hard** + **System Design** sections
4. **Staff/Principal**: Combine **Hard** + **System Design** + **Behavioral** questions
5. **Quick Review**: Use the [Cheat Sheets](./12-cheat-sheets/) before interviews

### Usage Examples

**By Company:**
```bash
# Search for questions known to be asked at Google
grep -r "Google" . --include="*.md"

# Search for questions asked at Amazon
grep -r "Amazon" . --include="*.md"
```

**By Topic:**
```bash
# Review all concurrency questions
cd 01-core-java/
cat 04-concurrency.md
```

**By Difficulty:**
```bash
# Study all Medium-level Spring Boot questions
grep -r "Difficulty: Medium" ./03-spring-boot/ --include="*.md"
```

## 📖 Question Format

Every question follows this standardized format for easy learning:

```markdown
## Question: [Clear Title]

**Category:** [Core Java / Spring Framework / etc.]
**Difficulty:** Easy / Medium / Hard
**Time to Answer:** 5-10 min / 15-20 min / 30+ min
**Companies:** [Google, Amazon, Netflix, etc.]

### Question
[Clear, specific question without ambiguity]

### Expected Answer Summary
[1-2 sentence summary of key points]

### Detailed Explanation
[Comprehensive explanation with reasoning]

### Code Example
[Practical, tested code]

### Key Takeaways
- Point 1
- Point 2
- Point 3

### Common Follow-Up Questions
- Follow-up 1
- Follow-up 2

### Related Topics
- [Link to related question]

### Sources
- [Citation with link]
```

## 🎓 Difficulty Levels Explained

| Level | Target Audience | Characteristics |
|-------|-----------------|-----------------|
| **Easy** | Junior developers, beginners | Basic concepts, definitions, simple patterns |
| **Medium** | Mid-level developers (3-5 yrs) | Real-world scenarios, trade-offs, optimization |
| **Hard** | Senior developers (5-10 yrs) | Complex architectures, edge cases, system-wide impact |
| **Staff** | Staff+ engineers (10+ yrs) | Strategic decisions, large-scale problems, mentoring |

## 💻 Code Examples

All code examples in this repository are:
- ✅ Tested and verified to compile/run
- ✅ Following Java best practices
- ✅ Documented with comments
- ✅ Real-world applicable

## 🏢 Companies Known to Ask These Questions

Questions are tagged with companies known to ask them:
- **FAANG**: Facebook/Meta, Apple, Amazon, Netflix, Google
- **Big Tech**: Microsoft, Apple, IBM, Oracle
- **Startups**: Airbnb, Uber, Spotify, DoorDash, Stripe
- **Fintech**: Goldman Sachs, Bloomberg, Robinhood
- **General**: Most companies ask fundamental questions

## 📊 Topic Coverage by Company

See [COMPANY_GUIDE.md](./COMPANY_GUIDE.md) for a breakdown of which topics are most important for different companies.

## 🔄 How This Was Built

This question bank is built using:
1. **Official Documentation** — Spring, Java, Jakarta EE specifications
2. **Established Repositories** — Tech Interview Handbook, System Design Primer
3. **Industry Experience** — Real interview experiences from top companies
4. **Community Contributions** — Improved and expanded by contributors

See [SOURCES.md](./SOURCES.md) for complete attribution and licensing information.

## 🤝 Contributing

We welcome contributions from the community! Whether you want to:
- Add new questions
- Improve existing answers
- Add code examples
- Fix errors or outdated information
- Improve documentation

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines.

## ⭐ How to Use This Repo Effectively

### For Daily Prep (30 minutes/day)
```
Week 1: Core Java basics (Easy questions)
Week 2: Spring Framework fundamentals
Week 3: Spring Boot + REST APIs
Week 4: Database & Transactions
Week 5: Security & Testing
Week 6: System Design + Performance
Week 7: Practice Hard questions + mock interviews
```

### For Interview the Day Before
- Review [Cheat Sheets](./12-cheat-sheets/)
- Skim key takeaways from your weak areas
- Practice 2-3 Hard questions in your target topic

### For Mock Interviews
1. Pick 3-4 random Hard questions
2. Answer without looking at solutions
3. Compare with provided answers
4. Note gaps in understanding

## 📈 Statistics

| Category | # Questions | Easy | Medium | Hard |
|----------|------------|------|--------|------|
| Core Java | 75 | 20 | 35 | 20 |
| Spring Framework | 60 | 15 | 30 | 15 |
| Spring Boot | 50 | 12 | 25 | 13 |
| Data Persistence | 65 | 15 | 35 | 15 |
| REST APIs | 45 | 12 | 20 | 13 |
| Security | 40 | 8 | 18 | 14 |
| Microservices | 55 | 10 | 25 | 20 |
| Testing | 45 | 15 | 20 | 10 |
| Performance/JVM | 50 | 10 | 25 | 15 |
| System Design | 55 | 5 | 20 | 30 |
| Behavioral | 35 | 20 | 10 | 5 |
| **TOTAL** | **575** | **142** | **263** | **170** |

## 🎁 Bonus Resources

- **[Cheat Sheets](./12-cheat-sheets/)** — Quick reference guides
- **[Code Snippets](./code-snippets/)** — Copy-paste ready solutions
- **[Mock Interviews](./mock-interviews/)** — Practice full interview scenarios
- **[Reading List](./READING_LIST.md)** — Recommended books and articles
- **[Company-Specific Prep](./COMPANY_GUIDE.md)** — Tailored for Google, Amazon, etc.

## ⚖️ License

This project is licensed under the **MIT License** — see [LICENSE](./LICENSE) file for details.

This means you can:
- ✅ Use for personal interview prep
- ✅ Share with friends and colleagues
- ✅ Modify and improve
- ✅ Use commercially
- ✅ Distribute

The only requirement is attribution (include the license file).

## 📝 Attribution

This project builds upon excellent open-source resources:
- [Interview-expert/spring-interview-questions](https://github.com/Interview-expert/spring-interview-questions) — MIT License
- [Tech Interview Handbook](https://github.com/yangshun/tech-interview-handbook) — MIT/CC0
- [System Design Primer](https://github.com/donnemartin/system-design-primer) — CC0
- Official Spring & Java documentation

See [SOURCES.md](./SOURCES.md) for complete attribution.

## 🐛 Issues & Feedback

Found an error? Have a question? Want to add content?
- 📥 Open an [Issue](https://github.com/hapreanmanuel/java-spring-interview-bank/issues)
- 📤 Submit a [Pull Request](https://github.com/hapreanmanuel/java-spring-interview-bank/pulls)
- 💬 Start a [Discussion](https://github.com/hapreanmanuel/java-spring-interview-bank/discussions)

## 🌟 Star History

If this repository helps you land your dream job, please consider giving it a star! It helps others discover this resource.

## 📧 Get Updated

- **Watch** this repository to get notified of updates
- **Star** it to show your support
- **Share** with friends and colleagues

---

**Last Updated:** 2026-10-01  
**Maintained by:** [hapreanmanuel](https://github.com/hapreanmanuel)  
**Contributing:** Yes, we welcome contributions!

Made with ❤️ for the Java/Spring community

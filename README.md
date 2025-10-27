# 🎯 Perfect Tense Mapper

An interactive visual timeline game for teaching and learning English perfect tenses. Students place actions on a timeline to understand the temporal relationships that make perfect tenses so challenging.

![Perfect Tense Timeline Game](https://img.shields.io/badge/Status-Active-success) ![Language](https://img.shields.io/badge/Language-JavaScript-yellow) ![License](https://img.shields.io/badge/License-MIT-blue)

## 📖 About

Perfect tenses are notoriously difficult for English language learners because they describe relationships between time points rather than simple past, present, or future. This game makes these abstract concepts concrete by letting students **physically place actions on a visual timeline**.

### Why This Works
- **Visual Learning**: See the duration and timing of actions
- **Interactive**: Drag and drop interface with immediate feedback
- **Progressive Hints**: Three-tier hint system from general to specific
- **Flexible Practice**: Filter by tense type, practice or game mode
- **Teaching Tool**: Blank mode lets teachers create custom examples in real-time

## ✨ Features

### 🎮 Three Game Modes

**📚 Practice Mode**
- Learn at your own pace
- No scoring pressure
- Toggle between showing/hiding marker types
- Perfect for self-study

**🏆 Game Mode**
- Timed challenges with scoring
- Test your knowledge
- Track your progress
- Great for competitive learners

**👨‍🏫 Blank Mode (Teaching Tool)**
- Create custom examples on the fly
- Adjustable timeline scales (minutes to years)
- Movable NOW marker
- Add custom reference points
- Perfect for classroom demonstrations

### 📊 Coverage

15 built-in questions covering:
- Simple Past/Present
- Present Perfect
- Present Perfect Continuous
- Past Perfect
- Past Perfect Continuous
- Future Perfect
- Future Perfect Continuous

### 🎯 Smart Features

- **Dynamic Timelines**: Automatically scales from minutes to years based on context
- **Flexible Validation**: Accepts approximate answers where appropriate
- **Progressive Hints**: Three-level hint system
- **Tense Filtering**: Practice specific tenses or mix them all
- **Randomization**: Different question order every time
- **Mobile Friendly**: Touch-optimized controls
- **Visual Feedback**: Color-coded correct/incorrect with answer overlays

## 🚀 Quick Start

### For Students/Teachers (Using the Game)

1. **Download** `perfect-tense-game.html`
2. **Open** it in any web browser (Chrome, Firefox, Safari, etc.)
3. **Select** a game mode and tenses to practice
4. **Start** playing!

No installation, no dependencies, no internet required after download.

### For Developers (Contributing)

```bash
# Clone the repository
git clone https://github.com/RomekaSolutions/Perfect-Tense-Mapper.git

# Open in your editor
cd Perfect-Tense-Mapper

# Open the HTML file in a browser
# That's it! It's a single-file application.
```

## 📝 How to Play

### Practice/Game Mode:

1. **Choose your mode** and select which tenses you want to practice
2. **Read the statement** (e.g., "I have been studying for 2 hours")
3. **Select marker type**: 
   - ⏱️ **Moment in Time** (for simple tenses - use a dot)
   - 📊 **Period of Time** (for perfect tenses - use a bar)
4. **Click on the timeline** to place your marker
5. **For bars**: Drag the handles to adjust the duration
6. **Submit** and get instant feedback!

### Blank Mode (Teachers):

1. Enter your own example sentence
2. Adjust the timeline scale (minutes/hours/days/months/years)
3. Set the timeline range
4. Position the NOW marker by dragging it
5. Add reference points for complex tenses (e.g., "before dinner")
6. Demonstrate the concept to students visually!

## 🎓 Educational Benefits

### For Students:
- **Visualize abstract concepts**: See why "I have lived" is different from "I lived"
- **Understand temporal relationships**: Grasp before/after/during with past/future perfect
- **Get immediate feedback**: Learn from mistakes with visual correction
- **Self-paced learning**: Practice mode removes pressure
- **Progressive support**: Hints guide without giving away the answer

### For Teachers:
- **Demonstrate concepts**: Use Blank Mode to show examples in real-time
- **Assess understanding**: Watch students place actions to see their thinking
- **Differentiated practice**: Students can filter by the tenses they need
- **No prep required**: Built-in question bank ready to use
- **Customizable**: Easy to add your own questions (see below)

## 📚 Adding Your Own Questions

Want to add more questions? It's easy!

1. Open `perfect-tense-game.html` in a text editor
2. Find the `QUESTION_BANK` array
3. Add a new question following this format:

```javascript
{
    id: 16,  // Next available number
    statement: "Your sentence here",
    tense: "present_perfect",  // See full list in documentation
    timelineScale: "years",    // minutes/hours/days/months/years
    timelineStart: 2010,
    timelineEnd: 2025,
    nowPosition: 2025,
    markerType: "bar",         // "bar" or "dot"
    correctAnswer: {
        type: "bar",
        start: 2020,
        end: 2025,
        flexible: true,
        validStartRange: [2018, 2022],
        validEndRange: [2025, 2025]
    },
    hints: [
        "General hint about the concept",
        "More specific guidance",
        "Direct instruction with answer type"
    ]
}
```

📖 **Full documentation**: See `question-guide.md` for detailed instructions and examples.

## 🛠️ Technical Details

- **Pure HTML/CSS/JavaScript** - No frameworks, no dependencies
- **Single File Application** - Easy to distribute and use offline
- **Responsive Design** - Works on desktop, tablet, and mobile
- **Touch Optimized** - Large hit targets for mobile users
- **Browser Compatibility** - Works in all modern browsers

## 🤝 Contributing

Contributions are welcome! Here are some ways you can help:

### 🐛 Found a Bug?
Open an issue with:
- Description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Browser and device info

### 💡 Have an Idea?
- Open an issue to discuss new features
- Check existing issues first to avoid duplicates

### ✍️ Want to Add Questions?
- Fork the repository
- Add questions following the format in `question-guide.md`
- Submit a pull request with your additions
- Include a brief description of the tenses/scenarios covered

### 🎨 Design Improvements?
- UI/UX enhancements
- Accessibility improvements
- Mobile optimizations

## 📋 Roadmap

Future enhancements we're considering:
- [ ] Export/import custom question banks
- [ ] Progress tracking and analytics
- [ ] Difficulty levels
- [ ] More languages
- [ ] Audio pronunciation support
- [ ] Printable worksheets generator
- [ ] Teacher dashboard with student progress

## 📄 License

MIT License - Feel free to use this in your classroom, modify it, or build upon it!

## 🙏 Acknowledgments

Created for English language teachers and learners who need a better way to visualize perfect tenses.

Special thanks to the ESL teaching community for inspiration and feedback.

## 📧 Contact

Questions? Suggestions? Open an issue or reach out!

---

**Made with ❤️ for English language learners everywhere**

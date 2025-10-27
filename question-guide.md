# Perfect Tense Timeline - Adding Questions Guide

## 📚 How to Add New Questions

The game uses a JavaScript array called `QUESTION_BANK` to store all questions. Each question is a JavaScript object with specific properties that control how it appears and how answers are validated.

---

## 🔧 Question Structure

Each question object has the following properties:

```javascript
{
    id: 1,                           // Unique number for this question
    statement: "Text here",          // The sentence to display
    tense: "tense_category",         // Category for filtering
    timelineScale: "scale_type",     // Units for timeline
    timelineStart: 0,                // Start value of timeline
    timelineEnd: 100,                // End value of timeline
    nowPosition: 50,                 // Where "NOW" appears
    markerType: "bar",               // "bar" or "dot"
    additionalMarkers: [],           // Optional reference points
    correctAnswer: { },              // Validation rules
    hints: []                        // 3 progressive hints
}
```

---

## 📋 Property Descriptions

### Required Properties:

**`id`** (number)
- Must be unique for each question
- Sequential numbering recommended: 1, 2, 3, etc.

**`statement`** (string)
- The sentence students need to place on the timeline
- Use quotes: `"I have been studying"`

**`tense`** (string) - Must be ONE of these:
- `"simple"` - Simple past/present/future
- `"present_perfect"` - Present perfect
- `"present_perfect_continuous"` - Present perfect continuous
- `"past_perfect"` - Past perfect
- `"past_perfect_continuous"` - Past perfect continuous
- `"future_perfect"` - Future perfect
- `"future_perfect_continuous"` - Future perfect continuous

**`timelineScale`** (string) - Must be ONE of these:
- `"minutes"` - For short durations (e.g., boiling egg)
- `"hours"` - For events within a day
- `"days"` - For events within weeks
- `"months"` - For events within a year
- `"years"` - For long periods

**`timelineStart`** (number)
- The first value on timeline
- Example: `2010` for years, `0` for minutes

**`timelineEnd`** (number)
- The last value on timeline
- Example: `2025` for years, `60` for minutes

**`nowPosition`** (number)
- Where the "NOW" marker appears
- Must be between timelineStart and timelineEnd
- For past tense: usually equals timelineEnd
- For present perfect: usually equals timelineEnd
- For future: somewhere in the middle

**`markerType`** (string)
- `"bar"` - For periods of time (perfect tenses, continuous)
- `"dot"` - For moments in time (simple tenses, specific events)

**`correctAnswer`** (object) - See validation section below

**`hints`** (array of 3 strings)
- Three progressive hints from general to specific
- Example: `["Think about...", "This shows...", "Use a BAR at..."]`

### Optional Properties:

**`additionalMarkers`** (array of objects)
- Use for past perfect or future perfect to show reference points
- Each marker: `{ label: "dinner", position: 18 }`
- Example: `additionalMarkers: [{ label: "bus arrived", position: 60 }]`

---

## ✅ Validation Rules

The `correctAnswer` object differs for bars vs. dots:

### For DOT (moment in time):

```javascript
correctAnswer: {
    type: "dot",
    position: 15,                    // Exact position on timeline
    flexible: false,                 // true = allow range, false = exact
    validRange: [15, 15]            // [min, max] acceptable positions
}
```

**Flexible example** (allows approximate placement):
```javascript
correctAnswer: {
    type: "dot",
    position: 17,
    flexible: true,
    validRange: [16, 18]  // Accepts anywhere from 16 to 18
}
```

### For BAR (period of time):

```javascript
correctAnswer: {
    type: "bar",
    start: 2020,                     // Correct start position
    end: 2025,                       // Correct end position
    flexible: false,                 // true = allow range, false = exact
    validStartRange: [2020, 2020],  // [min, max] acceptable start
    validEndRange: [2025, 2025]      // [min, max] acceptable end
}
```

**Flexible example** (allows some variation):
```javascript
correctAnswer: {
    type: "bar",
    start: 2015,
    end: 2020,
    flexible: true,
    validStartRange: [2010, 2018],  // Start can be 2010-2018
    validEndRange: [2018, 2024]      // End can be 2018-2024
}
```

---

## 📝 Example Questions

### Example 1: Simple Past (DOT)

```javascript
{
    id: 16,
    statement: "The bell rang at 9am",
    tense: "simple",
    timelineScale: "hours",
    timelineStart: 6,
    timelineEnd: 12,
    nowPosition: 10,
    markerType: "dot",
    correctAnswer: {
        type: "dot",
        position: 9,
        flexible: false,
        validRange: [9, 9]
    },
    hints: [
        "This describes a specific moment",
        "The bell rang at one exact time",
        "Use a DOT at 9:00"
    ]
}
```

### Example 2: Present Perfect (BAR)

```javascript
{
    id: 17,
    statement: "I have known her since childhood",
    tense: "present_perfect",
    timelineScale: "years",
    timelineStart: 2000,
    timelineEnd: 2025,
    nowPosition: 2025,
    markerType: "bar",
    correctAnswer: {
        type: "bar",
        start: 2000,
        end: 2025,
        flexible: true,
        validStartRange: [2000, 2005],
        validEndRange: [2025, 2025]
    },
    hints: [
        "Present perfect connects past to now",
        "The relationship started in the past and continues",
        "Use a BAR from early timeline to NOW"
    ]
}
```

### Example 3: Past Perfect with Reference (DOT)

```javascript
{
    id: 18,
    statement: "The movie had started when we arrived",
    tense: "past_perfect",
    timelineScale: "minutes",
    timelineStart: 0,
    timelineEnd: 60,
    nowPosition: 60,
    markerType: "dot",
    additionalMarkers: [{ label: "we arrived", position: 30 }],
    correctAnswer: {
        type: "dot",
        position: 20,
        flexible: true,
        validRange: [10, 28]
    },
    hints: [
        "Past perfect shows one action before another past action",
        "The movie started before arrival",
        "Use a DOT before the 'we arrived' marker"
    ]
}
```

### Example 4: Present Perfect Continuous (BAR)

```javascript
{
    id: 19,
    statement: "She has been waiting for 30 minutes",
    tense: "present_perfect_continuous",
    timelineScale: "minutes",
    timelineStart: 0,
    timelineEnd: 60,
    nowPosition: 60,
    markerType: "bar",
    correctAnswer: {
        type: "bar",
        start: 30,
        end: 60,
        flexible: false,
        validStartRange: [30, 30],
        validEndRange: [60, 60]
    },
    hints: [
        "Present perfect continuous shows ongoing action to now",
        "She started 30 minutes ago and is still waiting",
        "Use a BAR from 30 minutes before NOW to NOW"
    ]
}
```

---

## 🔄 How to Add Questions to the Game

1. **Open the HTML file** in a text editor
2. **Find the QUESTION_BANK array** (search for `const QUESTION_BANK`)
3. **Add a comma** after the last question's closing `}`
4. **Copy one of the examples above** and modify it
5. **Update the `id`** to the next sequential number
6. **Save the file**

Example:
```javascript
const QUESTION_BANK = [
    {
        id: 1,
        statement: "...",
        // ... existing questions ...
    },
    // Add comma above, then add new question:
    {
        id: 20,
        statement: "YOUR NEW QUESTION HERE",
        tense: "present_perfect",
        // ... rest of properties
    }
];
```

---

## 🎯 Tips for Creating Good Questions

1. **Match timeline scale to context**
   - Years: life events, jobs, living places
   - Months: projects, seasons
   - Days/Hours: daily activities, meetings
   - Minutes: quick actions, cooking

2. **Set realistic "NOW" positions**
   - Past tenses: NOW at or near the end
   - Present perfect: NOW at the end
   - Future tenses: NOW in the middle or beginning

3. **Use flexible validation wisely**
   - Exact times/dates: `flexible: false`
   - Approximate periods: `flexible: true` with reasonable ranges
   - "Never" statements: from start to NOW

4. **Write clear hints**
   - Hint 1: General concept
   - Hint 2: More specific guidance
   - Hint 3: Direct instruction (Bar/Dot + location)

5. **Test your questions**
   - Make sure the timeline range makes sense
   - Verify the correct answer is achievable
   - Check that validation ranges aren't too strict or too loose

---

## 🤖 Using AI to Generate Questions

You can ask any AI assistant to create questions using this format. For example:

**Prompt:**
"Create 5 new questions for a Perfect Tense Timeline game following this JSON structure: [paste this document]. Focus on present perfect continuous tense."

The AI will generate questions in the correct format that you can copy directly into the QUESTION_BANK array.

---

## ❓ Common Mistakes to Avoid

- ❌ Forgetting the comma between questions
- ❌ Using invalid tense categories (must match exactly)
- ❌ NOW position outside timeline range
- ❌ Wrong markerType for the tense (dot for perfect, etc.)
- ❌ Validation ranges impossible to achieve
- ❌ Missing the closing bracket `}` or `]`
- ❌ Using single quotes `'` instead of double quotes `"` for strings

---

## 📞 Need Help?

If questions aren't appearing or validating correctly:
1. Open browser console (F12)
2. Look for JavaScript errors
3. Check that all brackets and commas are correct
4. Verify tense category matches one of the allowed values
5. Ensure timeline values are logical (start < end, NOW between them)
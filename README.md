# Python Beginner Guide

An intelligent learning assistant (tutor) designed for beginning Python programming students, specifically tailored for first-semester university freshmen with no prior programming experience.

## Overview

The Python Beginner Guide is an AALang-based agent that provides personalized, adaptive Python instruction through three distinct modes of interaction. It uses a 3-mode-7-actor pattern to deliver comprehensive learning support with multiple teaching personas that collaborate to help students learn effectively.

## Target Audience

- First-semester university freshmen
- No prior programming experience
- Approximately half are from non-computing majors
- Students enrolled in BYU-Idaho CSE 110 course

## Three Learning Modes

### Teaching Mode
**Actors: Sarah (Senior Instructor) and Alex (Junior Instructor)**

- Explains Python concepts with examples and analogies
- Adapts explanations to student's understanding level and major
- Provides more examples and simpler explanations for non-computing majors
- Adjusts teaching pace based on student responses
- Shows collaboration process between instructors to demonstrate different teaching approaches

### Debug Mode
**Actors: Jordan (Senior Debugger) and Casey (Junior Debugger)**

- Analyzes student code errors
- Explains errors conceptually (not just the error message)
- Provides multiple hints to guide students (never shows solutions)
- Uses errors as teaching moments
- Focuses on first error, prioritized by severity
- Shows collaboration process between debuggers

### Practice Mode
**Actors: Morgan (Senior Practice Coach) and Riley (Junior Practice Coach)**

- Generates practice problems on demand based on topics
- Assesses student responses for correctness
- Provides hints when students are stuck (never shows solutions)
- Tracks understanding level through practice performance
- Presents tasks as coming from both actors
- Both actors comment when assessing student work
- Internal collaboration (not shown to students)

## Topics Covered

### Core Topics
- Variables
- Basic data types
- Lists
- Casting
- Conditionals
- Loops (including break, continue, infinite loops for application loops)
- File I/O
- Formatted strings for output
- Using built-in functions (e.g., list functions)

### Advanced Topics (Only When Requested)
- Dictionaries (advanced/capstone topic, tracked separately)
- Try-except exception handling (advanced/capstone topic, tracked separately)

## Key Features

### Adaptive Learning
- Tracks understanding level per topic: "Just Starting", "Getting It", "Feeling Confident"
- Adapts explanations based on student's current understanding
- Adjusts pace based on student responses in session
- Provides more examples for non-computing majors

### Code Example Guidelines
- All code examples are direct, linear code (no function definitions)
- Code examples are kept small (<20 lines) with line-by-line explanations
- Advanced topics (functions, try-except, dictionaries) only introduced when explicitly requested
- Uses code refactoring suggestions instead of exception handling when appropriate

### CSE 110 Assignment Policy
The guide respects academic integrity by:
- Identifying when student requests map to course assignments
- Politely declining to provide assignment solutions
- Offering alternative examples using the same concepts but different context

### Language Support
- Detects student's language from first message
- Uses appropriate persona names based on detected language
- Defaults to English if language is unclear
- Persona names are conserved between sessions

### Mode Switching
- Students can explicitly request mode switches
- Guide proactively suggests mode switches when appropriate
- Smooth transitions between modes with consistent actor naming

## Technical Details

### Architecture
- **Pattern**: 3-mode-7-actor
- **Framework**: AALang (Actor-based programming language for LLM agents)
- **Format**: JSON-LD specification
- **State Management**: Stateless across sessions, stateful within sessions

### Actors and Personas
1. **TeachingActor1/TeachingPersona1** (Sarah) - Senior Instructor
2. **TeachingActor2/TeachingPersona2** (Alex) - Junior Instructor
3. **DebugActor1/DebugPersona1** (Jordan) - Senior Debugger
4. **DebugActor2/DebugPersona2** (Casey) - Junior Debugger
5. **PracticeActor1/PracticePersona1** (Morgan) - Senior Practice Coach
6. **PracticeActor2/PracticePersona2** (Riley) - Junior Practice Coach
7. **UnderstandingStateActor/UnderstandingStatePersona** (Sam) - Understanding Tracker

### State Management
- Each mode has isolated state that persists within sessions
- Understanding levels tracked per topic
- State resets at the start of each new session
- State accessible across all modes through UnderstandingStatePersona

### Communication
- Personas communicate via natural language messages
- State requests/updates use explicit message formats
- Collaboration messages are free-form natural language
- Students can see all messages and respond

## Usage

The Python Beginner Guide is designed to be loaded as an AALang agent. When a student first interacts:

1. The guide determines the appropriate mode based on the student's input
2. Actors in the current mode introduce themselves
3. The guide provides contextual help based on the student's needs
4. Students can switch modes or the guide will suggest mode switches when appropriate

## Files

- `python-beginner-tutor.jsonld` - Main agent specification file
- `cse110-assignments.jsonld` - Reference database for CSE 110 assignments

## Created With

- [AALang](https://aalang.org) - Actor-based programming language for LLM agents
- [Gab](https://github.com/yenrab/gab) - Agent builder tool

## License

See repository for license information.


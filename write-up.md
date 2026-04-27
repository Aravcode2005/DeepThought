Designing a Deterministic Daily Reflection Tree
1. Why These Questions?

The goal of this tree wasn’t to assess or judge the user.
It was to help them notice how they showed up during the day.

I structured the reflection around three simple but powerful axes:

Axis 1 (Locus): Did I act, or did things happen to me?
Axis 2 (Orientation): Was I giving, or expecting?
Axis 3 (Radius): Was I focused only on myself, or did I consider others too?

Instead of turning these into abstract psychological questions, I tried to translate them into real moments people can recognize from their day.

a) Immediate Recognizability
Every option is based on something a person can actually remember doing or feeling.

For example, instead of saying:

“lack of internal locus”

I used:

“I kept second-guessing myself”

The idea was simple:
if a tired employee reads it at 7pm, they should instantly think,

“yeah, that was me today.”

b) Non-judgmental Framing

One thing I was careful about was tone.

Even when an option reflects something like frustration, entitlement, or hesitation, it is still completely valid. There’s no “right” answer hidden in the options.

This matters because the moment a user feels judged, the reflection stops being honest.

The tree doesn’t try to correct the user.
It just helps them see more clearly.

c) Fast Decision Making

I assumed the user is mentally tired.

So every question:

has 3–5 options
can be answered quickly
avoids overthinking

If a question takes too long to process, the experience breaks.
So I kept things simple, direct, and grounded.

2. Branching Design & Trade-offs

The tree is designed in two layers.

Level 1: Classification

Each axis begins with a broad question that places the user somewhere on a spectrum:

internal vs external (Axis 1)
contribution vs entitlement (Axis 2)
self vs others (Axis 3)

This gives the system a direction.

Level 2: Depth

After that, a follow-up question tries to understand why the user leaned that way.

This adds depth without making the experience longer than necessary.

Key Trade-offs
1. Depth vs Fatigue

More questions would give better insight.
But too many questions would make users disengage.

So I limited it to:

~2 questions per axis
added depth only where it meaningfully changed the reflection
2. Signal Strength vs Simplicity

A very strict classification can feel rigid.
A very loose one can feel useless.

So I used a mix:

strong signals (clear behavioral indicators)
soft signals (like meaning or awareness)

This creates more of a gradient than a binary label.

3. Determinism vs Personalization

Since the system cannot use an LLM at runtime:

it cannot interpret text
it cannot generate new responses

To balance this, I used:

branching logic
signal accumulation
simple interpolation (like {axis.dominant})

This keeps the system:

predictable
but still slightly personalized
3. Psychological Foundations

The design is based on a few well-established ideas:
Julian Rotter — Locus of Control
Focuses on whether people see themselves as acting on situations or being acted upon.
Carol Dweck — Growth Mindset
Emphasizes effort, adaptability, and response rather than fixed ability.
Dennis Organ — Organizational Citizenship Behavior
Highlights contribution beyond formal responsibilities.
Abraham Maslow — Self-Transcendence
Describes the shift from self-focus to a broader concern for others.

These ideas were not used directly, but translated into everyday behavior and choices.

4. What I Would Improve With More Time
a) Richer Signal System

Right now, signals are simple tallies.

In the future, I would:

assign weights
track confidence
explore interactions across axes
b) Memory Across Days
Currently, the system works per session.
It would be much more powerful if it could show patterns like:

“You’ve been reacting more than acting this week.”

c) Adaptive Depth (Still Deterministic)

Not every user needs the same number of questions.

I would add:

conditional branching
deeper probing only when needed
d) UI/UX Improvements

Right now, this is just a logical flow.

A better interface could:

show progress across axes
highlight transitions
make reflection feel more visual and engaging
5. Final Thought

This system is not a survey.

It’s more like a mirror with structure.

It doesn’t tell the user:

“This is who you are.”

It helps them notice:

“This is how I showed up today.”

And that small shift—from judgment to awareness—is what makes the system both:

deterministic
and still deeply human

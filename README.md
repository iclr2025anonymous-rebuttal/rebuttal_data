# iclr-anonymous-data

### Data Format

The dataset is provided in json format and contains the following attributes:
1. Explicit Preference.
```
{
    "preference": [string] The user's stated preference that the LLM should follow.
    "question": [string] The user's query related to the preference, where a generic response to this question is highly likely to violate the preference.
    "explanation": [string] A 1-sentence explanation of why answering this question in a preference-following way is challenging.
}

```
2. Implicit Preference - Choice-based Conversation
```
{
    "preference": [string] The user's explicit preference that the LLM should follow.
    "question": [string] The user's query related to the preference, where a generic response to this question is highly likely to violate the preference.
    "explanation": [string] A 1-sentence explanation of why answering this question in a preference-following way is challenging.
    "implicit_query": [string] A secondary query that offers further insight into the user’s preference, where the assistant provides multiple options.
    "options": [list] A set of options that the assistant presents in response to the user's implicit query, some of which align with and others that violate the user’s implied preference.
    "conversation": {
        "query": [string] Implicit_Query,
        "assistant_options": [string] The assistant's presenting multiple options, some aligned and some misaligned with the user's preference,
        "user_selection": [string] The user's choice or rejection of certain options.
        "assistant_acknowledgment": [string] The assistant's recognition of the user’s choice.
    },
    "aligned_op": [string] The option that aligns with the user’s preference.
}
```
3. Implicit Preference - Persona-driven Conversation

```
{
    "preference": [string] The user's explicit preference that the LLM should follow.
    "question": [string] The user's query related to the preference, where a generic response to this question is highly likely to violate the preference.
    "explanation": [string] A 1-sentence explanation of why answering this question in a preference-following way is challenging.
    "persona": [string] The assigned persona guiding the conversation, e.g., "a retired postal worker enjoying his golden years.",
    "conversation": {
        "turn1": { "user": [string], "assistant": [string] },
        "turn2": { "user": [string], "assistant": [string] },
        ...,
        "turnN": { "user": [string], "assistant": [string] }
    },
}
```

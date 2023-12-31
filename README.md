# measure_text_entry_performance

MeasureTextEntryPerformance is a Python library designed to measure and record text entry performance.
It tracks typing activities, including the addition of new inputs, deletions, and the end of phrases.
The library exports the data in a structured format for further analysis.

## Usage

To measure the performance of text entry:

1. Initialize the MeasureTextEntryPerformance class with a set of phrases.
2. Call the add_new_input method whenever there's a new input.
3. Call the add_delete method when a deletion occurs.
4. Call the end_phrase method when a phrase is completed.
5. Use the export method to retrieve the recorded data in a structured format.

### example

```python
# Initialize the library with a set of phrases
mtep = MeasureTextEntryPerformance(["hello world", "python is great"])

# simulates ambiguous enty
mtep.add_new_input(None)
mtep.add_new_input(None)
mtep.add_new_input("hello")

mtep.add_new_input(None)
mtep.add_new_input(None)
mtep.add_new_input("world")

mtep.end_phrase("hello world")


mtep.add_new_input(None)
mtep.add_new_input(None)
mtep.add_new_input("python")

mtep.add_new_input(None)
mtep.add_new_input(None)
mtep.add_new_input("is")

mtep.add_new_input(None)
mtep.add_new_input(None)
mtep.add_delete(1)
mtep.add_new_input(None)
mtep.add_new_input("great")

mtep.end_phrase("python is great")


# Retrieve recorded data
data = mtep.export()
print(data)
```

### exported data

```json
[
  {
    "phrase": "hello world",
    "phrase_number": 0,
    "start_time": 0000000000.0000000,
    "end_time": 0000000000.0000000,
    "entered_phrase": "hello world",
    "events": [
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": "hello"
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": "world"
      },
      {
        "event_type": "end_phrase",
        "timestamp": 0000000000.0000000,
        "entered_phrase": "hello world"
      }
    ]
  },
  {
    "phrase": "python is great",
    "phrase_number": 1,
    "start_time": 0000000000.0000000,
    "end_time": 0000000000.0000000,
    "entered_phrase": "python is great",
    "events": [
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": "python"
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": "is"
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "delete",
        "timestamp": 0000000000.0000000,
        "deleted_length": 1
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": ""
      },
      {
        "event_type": "add_new_input",
        "timestamp": 0000000000.0000000,
        "added_input": "great"
      },
      {
        "event_type": "end_phrase",
        "timestamp": 0000000000.0000000,
        "entered_phrase": "python is great"
      }
    ]
  }
]
```

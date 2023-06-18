# General python reference notes

## Setting up new python project

**Setup virtual environment (linux)**
- `python3 -m venv .venv`
- `source .venv/bin/activate`
- `pip install -r requirements.txt`
- Example of `requirements.txt`:

  ```
  discord.py==2.2.2
  python-dotenv==1.0.0
  ```
- `.gitginore` contents:

  ```
  __pycache__
  venv
  ```


# Backend Code Style Guide

**Student ID:** 832301327  
**Project:** Contacts Management Web App (Backend)  
**Course:** EE308  

**Sources of Code Style Standards (Required by Assignment):**
- PEP 8 – Style Guide for Python Code  
  https://peps.python.org/pep-0008/
- Django Official Coding Style Guidelines  
  https://docs.djangoproject.com/en/stable/internals/contributing/writing-code/coding-style/
- Google Python Style Guide (referenced for docstring formatting)  
  https://google.github.io/styleguide/pyguide.html

---

## 1. General Principles
- Code must be **clear, readable, maintainable, and consistent**.
- Keep functions **focused**; each function should do one thing well.
- Avoid redundancy and unnecessary complexity.
- Name variables and functions clearly so that intent is obvious.
- Use comments to explain **why**, not what the code does.

---

## 2. Directory and File Organization
- Follow Django’s recommended MVC (Model–Template–View) structure.
- One Django **app** should represent **one domain concept** (here: `contacts_app`).
- Keep models, views, serializers, and URLs separated logically.

contacts_app/
├── models.py        # Database models
├── views.py         # View functions / class-based API methods
├── serializers.py   # DRF serializers (if used)
├── urls.py          # Routing for this app
└── tests.py         # Unit tests

---

## 3. Python Style Rules (PEP 8)

### Indentation & Formatting
- Use **4 spaces** for indentation (no tabs).
- Maximum line length: **100 characters**.
- Leave **one blank line** between functions.
- Leave **two blank lines** between top-level class or function definitions.

### Naming Conventions
| Type | Style | Example |
|------|-------|---------|
| Variables & Functions | `snake_case` | `get_contact_list()` |
| Classes | `PascalCase` | `ContactViewSet` |
| Constants | `UPPER_CASE` | `DEFAULT_LIMIT = 50` |

### Imports
- Use **absolute imports**, not relative.
- Group imports like this:

Standard library imports
Third-party library imports
Django imports
Local application imports

Example:
```python
import json
from django.http import JsonResponse
from rest_framework.views import APIView
from .models import Contact


⸻

4. Django Best Practices

Models (models.py)
	•	Each model should represent one real-world entity.
	•	Use descriptive field names and include blank=False and null=False unless needed.
	•	Always define __str__(self) for readability in admin and debugging.

Views (views.py)
	•	Use class-based views or DRF ViewSets when possible for cleaner organization.
	•	Return JSON responses in a consistent structure.

Serializers (serializers.py)
	•	Validate data here, not in the views.
	•	Keep input/output transformation centralized.

URLs (urls.py)
	•	Keep routes clean and REST-like:

/contacts/
/contacts/<id>/



⸻

5. JavaScript API Integration (Frontend <-> Backend)
	•	Always use JSON for request and response bodies.
	•	Backend must include correct response codes (200, 201, 400, 404).
	•	Always return meaningful error messages.

⸻

6. Comments & Documentation
	•	Use comments to explain intent, not obvious behavior.
	•	Follow Google-style docstrings:

def get_contact(id):
    """
    Retrieve a single contact by ID.

    Args:
        id (int): The primary key of the contact.

    Returns:
        Contact object or None.
    """


⸻

7. Testing
	•	Write tests in tests.py for:
	•	Model validation
	•	API endpoint responses
	•	Edge cases (empty inputs, invalid data)

Example:

from django.test import TestCase
from .models import Contact

class ContactModelTest(TestCase):
    def test_create_contact(self):
        c = Contact.objects.create(name="Test", email="test@test.com", phone="123")
        self.assertEqual(c.name, "Test")


⸻

8. Version Control (Git)
	•	Commit messages should be clear and descriptive:
	•	✅ Added POST /contacts endpoint validation
	•	❌ fix stuff

⸻

9. Summary

Following these standards ensures your backend:
	•	Is professionally structured
	•	Matches industry best practices
	•	Is easy to review and grade
	•	Works cleanly with your frontend

⸻

End of codestyle.md

---

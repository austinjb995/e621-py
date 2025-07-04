# e621-py (Fork by austinjb995)

A maintained and Flask-compatible fork of the original [`e621-py`](https://github.com/eoan-ermine/e621-py), a Python 3 wrapper for the [e621 API](https://e621.net/help/api). This version contains improvements for better schema compatibility, Flask integration, and ease of use via environment variables.

---

## 🚀 Why This Fork?

This fork introduces key modifications to address stability, extensibility, and modern application integration:

- ✅ **Validation Error Fixes**  
  Patched the `Post` model to tolerate missing `sample.alternates.original` fields in e621 responses, preventing runtime `ValidationError` issues.

- ✅ **Expanded User Model**  
  Extended the `AuthenticatedUser` model to support attributes required for filtering by blacklist and user preferences.

- ✅ **Environment Variable Authentication**  
  Credentials can now be provided securely via `.env` instead of hardcoding in code.

- ✅ **JSON Serialization Support**  
  Adds support for exporting search results to JSON using Pydantic’s `.dict()` method and a custom serializer to handle sets.

- ✅ **Web App Friendly**  
  Optimized for integration into Flask-based apps, including helper methods for tag queries, downloading post media, and rendering templates.

---

## 🛠 Installation

```bash
pip install git+https://github.com/austinjb995/e621-py.git

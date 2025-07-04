## 🔧 About This Fork

This fork of [`e621-py`](https://github.com/eoan-ermine/e621-py) was created to resolve compatibility issues with live API responses and to better integrate the library into Flask-based web applications. The original library is robust but lacked support for some evolving API schema changes and serialization workflows required for frontend integration.

### ✅ Fork Enhancements

#### 1. **📌 Fixed `AuthenticatedUser` Validation Errors**
The live e621 API now returns several additional fields not present in the upstream `AuthenticatedUser` model. These missing fields caused `pydantic.ValidationError` crashes at runtime.

**Fix:**
- Added the following as `Optional` fields:
  - `show_avatars`
  - `blacklist_avatars`
  - `has_saved_searches`
  - `disable_mobile_gestures`
  - `disable_post_tooltips`
  - `no_feedback`

#### 2. **📌 Patched `Post` Model to Support Nested `alternates.original`**
Some posts returned `sample.alternates.original` with `type` and `urls`, which were previously unmodeled.

**Fix:**
- Added nested `AlternateVersion`, `SampleAlternates`, and updated the `Sample` model to support:
```json
"sample": {
  "alternates": {
    "original": {
      "type": "...",
      "urls": ["..."]
    }
  }
}

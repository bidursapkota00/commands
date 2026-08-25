## Others

### Convert ipynb to markdown

```bash
jupyter nbconvert --to markdown *.ipynb

for %f in (*.ipynb) do jupyter nbconvert --to markdown "%f"

# macos - recursive folders
find . -name "*.ipynb" -exec jupyter nbconvert --to markdown {} \;
```

- **Description:** Converts all ipynb files in current folder to markdown.

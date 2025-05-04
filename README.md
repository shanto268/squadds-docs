# SQuADDS Documentation

This repository contains the documentation for the SQuADDS package. The documentation is built using Sphinx and hosted on Read the Docs.

## Local Development

1. Install the required dependencies:

   ```bash
   pip install -r docs/requirements.txt
   ```

2. Get the tutorials from the SQuADDS repository:

   ```bash
   # Clone the SQuADDS repository (if you haven't already)
   git clone https://github.com/LFL-SQuADDS/SQuADDS.git ../SQuADDS

   # Create tutorials directory in docs/source if it doesn't exist
   mkdir -p docs/source/tutorials

   # Copy tutorials and associated files
   cp ../SQuADDS/tutorials/Tutorial*.ipynb docs/source/tutorials/
   cp ../SQuADDS/tutorials/*.png docs/source/tutorials/
   ```

3. Build the documentation locally:

   ```bash
   cd docs
   make html
   ```

4. View the built documentation:
   ```bash
   open _build/html/index.html
   ```

## Documentation Structure

- `docs/`: Contains all documentation source files
- `docs/conf.py`: Sphinx configuration file
- `docs/requirements.txt`: Documentation-specific dependencies including SQuADDS
- `.readthedocs.yml`: Read the Docs configuration

## Version Management

The documentation is versioned alongside the main SQuADDS package. Each release of SQuADDS should have corresponding documentation updates in this repository.

- Documentation versions are maintained using git tags
- The documentation automatically pulls in the specified version of SQuADDS as a dependency
- To update documentation for a new SQuADDS version:
  1. Update the SQuADDS version in `docs/requirements.txt`
  2. Make necessary documentation updates
  3. Create a new tag matching the SQuADDS version

## Version Controlling Documentation

To enable version controlling in the documentation:

1. Add the following to your `docs/conf.py`:

   ```python
   # Version controlling configuration
   html_theme_options = {
       'navbar_end': ['version-switcher'],
       'switcher': {
           'json_url': 'https://raw.githubusercontent.com/LFL-SQuADDS/squadds-docs/main/docs/_static/switcher.json',
           'version_match': 'latest',
       },
       'check_switcher': False,
   }
   ```

2. Create a `docs/_static/switcher.json` file with your version information:

   ```json
   {
     "versions": [
       {
         "name": "latest",
         "version": "latest",
         "url": "https://squadds-docs.readthedocs.io/en/latest/"
       },
       {
         "name": "v0.1.0",
         "version": "v0.1.0",
         "url": "https://squadds-docs.readthedocs.io/en/v0.1.0/"
       }
     ]
   }
   ```

3. Update the switcher.json file whenever you create a new version tag.

## Contributing

1. Make changes to the documentation files in the `docs/` directory
2. Build and test locally
3. Commit and push changes
4. Read the Docs will automatically build and deploy the updated documentation

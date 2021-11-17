# Install steps

    python3 -m venv .venv
    source .venv/bin/activate
    pip install pip wheel setuptools
    pip install -r requirements.txt

    # and build (fr) HTML
    make -e SPHINXOPTS="-v -D language='fr'" html

    # open HTML in the browser
    xdg-open build/html/index.html

    # build (en) HTML and reload page in the browser
    make -e SPHINXOPTS="-v -D language='en'" html

# create POT locales/index.pot

    sphinx-build -M gettext -d "build/.doctrees" source source/locales

# create fr translation in locales/fr/LC_MESSAGES/index.po

    sphinx-intl update -l fr -d source/locales -p source/locales

# Uninstall steps

    deactivate
    rm -rf .venv build source/locales

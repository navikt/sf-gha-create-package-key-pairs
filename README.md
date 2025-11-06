# sf-gha-create-package-key-pairs

Denne actionen lager en package key pair string på formatet `packageA:key packageB:key`.

Forutsetninger:

* Allerede autentisert mot en devhub
* SF cli allerede installert

Flyt:

1. Tar imot en package key og path til en sfdx-project.json fil.
2. Henter liste over alle pakkeversjoner Dev Hub.
3. Sammenligner med pakker i sfdx-prject.json.
4. Bygger key-pair stringen for de pakker som krever en package key.


## Bruk

<!-- Start usage -->
```yaml
- id: generate-package-keys
  uses: navikt/sf-gha-create-package-key-pairs@<tag/sha>
    with:
        # Path to sfdx-project.json
        # Required: true
        sfdx-project-path: ''

        # Installation key to apply to password-protected dependencies
        # Required: true
        package-key: ''

        # Alias of the Dev Hub org to use for retrieving package version information
        # Required: false
        # Default: 'dev-hub'
        devhub-alias: ''

        # Enable debug logging output
        # Required: false
        # Default: 'false'
        debug: ''

- run: |
    sf install packages -key "$SFP_PACKAGE_KEY_PAIRS"
  env:
    SFP_PACKAGE_KEY_PAIRS: "${{ steps.generate-package-keys.outputs.package-keys }}"
```
<!-- end usage -->

## Henvendelser

Spørsmål knyttet til koden eller prosjektet kan stilles som issues her på GitHub.

## For NAV-ansatte

Interne henvendelser kan sendes via Slack i kanalen #platforce.

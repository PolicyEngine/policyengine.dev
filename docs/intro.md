# PolicyEngine Developer Guide

This book contains a guide for development of PolicyEngine repositories, covering code conventions, styles and general patterns. 
All the repositories are housed under the [PolicyEngine GitHub organisation](https://github.com/PolicyEngine). 
The repositories have the following dependency structure:

* **PolicyEngine**: Code for the front-end React app, and the back-end API
    * **OpenFisca-UK**: A tax-benefit microsimulation model of the UK, with implementations for policy rules
        * **OpenFisca-UK-Data**: A Python package for generating and storing microdata for OpenFisca-UK
        * **OpenFisca-Tools**: A Python package containing common classes used to enhance OpenFisca country packages
    * **OpenFisca-US**: A model for the US, as above
        * **OpenFisca-US-Data**: A package for managing microdata for OpenFisca-US, similar to OpenFisca-UK-Data
        * **OpenFisca-Tools**: As above

All of our code powering PolicyEngine is open-source, and all contributions and contributors are welcome. 
If you'd like to get involved, open a PR or issue or feel free to reach out at [contact@policyengine.org](mailto:contact@policyengine.org).

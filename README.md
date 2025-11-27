# PCIe Configuration Space Viewer

A single-file, interactive HTML5 application for visualizing and exploring PCIe Configuration Space headers, Capabilities, and Extended Capabilities.

## Contributing

We welcome contributions to add more PCIe Capabilities and Extended Capabilities!

### How to Add a New Capability

All data is defined in the `structures` array within `index.html`. To add a new capability, follow these steps:

1.  **Open `index.html`** in your text editor.
2.  **Locate the `structures` array** in the JavaScript section.
3.  **Append a new object** to the array following this template:

```javascript
{
  id: "unique_id_for_capability", // e.g., "ltr_extcap"
  type: "Cap" | "ExtCap",         // "Cap" for PCI Capabilities, "ExtCap" for Extended
  name: "Capability Name",        // e.g., "Latency Tolerance Reporting"
  description: "Brief description from the spec.",
  rows: [
    // Define the layout of registers (visual map)
    {
      offset: "00h", // Relative offset within the capability
      fields: [
        // Define fields within this row (total width must be <= 32 bits)
        { id: "field_id", label: "Field Label", range: "[31:0]" }
      ]
    },
    // Add more rows as needed...
  ],
  bitfields: {
    // Define detailed bit descriptions for each field defined above
    field_id: {
      name: "Field Name",
      offset: "00h",
      range: "[31:0]",
      bits: [
        // Define individual bits or ranges
        {
          range: "[0]",
          title: "Bit Name",
          description: "Description of what this bit does.",
          values: { "0": "Meaning of 0", "1": "Meaning of 1" } // Optional value meanings
        },
        {
          range: "[31:1]",
          title: "Reserved",
          description: "Reserved."
        }
      ]
    }
  }
}
```

4.  **Save and Refresh:** Open `index.html` in your browser to verify the new capability appears in the list and renders correctly.

### Contributing Back

We encourage you to contribute your changes back to the master branch!

1.  **Fork** the repository on GitHub.
2.  **Clone** your fork locally.
3.  **Create a new branch** for your feature (e.g., `git checkout -b add-ltr-capability`).
4.  **Commit** your changes (e.g., `git commit -m "feat: Add LTR Extended Capability"`).
5.  **Push** to your branch (e.g., `git push origin add-ltr-capability`).
6.  **Open a Pull Request** against the `master` branch of the original repository.

Please ensure your code follows the existing style and that all comments are in English.

### Localization

Please ensure all comments and user-facing text are in **English**.

## License

This project is licensed under the Mozilla Public License 2.0 (MPL 2.0). See the `LICENSE` file for details.

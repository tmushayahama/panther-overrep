# OverrepForm Component

A customizable form component built with StencilJS for gene overrepresentation analysis. This component provides an interface for users to input gene IDs and select ontology options, with support for example data and customizable styling.

## Features

- Gene ID input textarea with configurable rows
- Ontology selection dropdown
- Example data population
- Customizable labels and hints
- Flexible submission handling (URL or event-based)
- Comprehensive CSS theming support
- Shadow DOM encapsulation

## Installation

### NPM

```bash
npm install overrep-form
```

### CDN

```html
<script type="module" src="https://unpkg.com/overrep-form@latest/dist/panther-overrep-form/panther-overrep-form.esm.js"></script>
```

## Usage

### Basic HTML

```html

    <script type="module" src="https://unpkg.com/overrep-form@latest/dist/panther-overrep-form/panther-overrep-form.esm.js"></script>
    <style>
        /* Component styles */
        overrep-form {
            /* Layout */
            --overrep-width: 100%;
            --overrep-height: 450px;
            
            /* Colors */
            --overrep-primary-color: #4a90e2;
            --overrep-secondary-color: #f5f6f7;
            --overrep-text-color: #333333;
            --overrep-border-color: #e1e4e8;
            
            /* Typography */
            --overrep-font-size: 16px;
            
            /* Spacing */
            --overrep-form-spacing: 1.5rem;
            --overrep-border-radius: 8px;
            
            /* Add shadow */
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
    </style>
    <div class="form-container">
        <overrep-form
            ontology-options='[
                {"id": "biological_process_IBA", "label": "biological process PAN-GO"},
                {"id": "molecular_function_IBA", "label": "molecular function PAN-GO"},
                {"id": "cellular_component_IBA", "label": "cellular component PAN-GO"}
            ]'
            example-genes='["AKT1", "BDNF", "CCKAR", "CHI3L1"]'
            submit-url="/api/overrep"
            species="HUMAN"
            test-type="FISHER"
            ontology-label="Choose Ontology Type"
            gene-ids-label="Input Gene IDs"
            submit-label="Run Analysis"
            examples-label="Use Example Set"
            show-hint="true"
            hint="Accepts gene symbols and IDs"
        ></overrep-form>
    </div>
></overrep-form>
```

### React

```jsx
import { OverrepForm } from 'overrep-form';

const App = () => {
  const ontologyOptions = [
    { id: "biological_process_IBA", label: "biological process PAN-GO" },
    { id: "molecular_function_IBA", label: "molecular function PAN-GO" },
    { id: "cellular_component_IBA", label: "cellular component PAN-GO" }
  ];

  const exampleGenes = [
    "AKT1", "BDNF", "CCKAR", "CHI3L1", "CHRNA7",
    "CLDN5", "CNR1", "COMT"
  ];

  return (
    <OverrepForm
      ontologyOptions={ontologyOptions}
      exampleGenes={exampleGenes}
      submitUrl="/api/overrep"
    />
  );
};
```

### Angular

```typescript
// app.module.ts
import { CUSTOM_ELEMENTS_SCHEMA, NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  schemas: [CUSTOM_ELEMENTS_SCHEMA]
})
export class AppModule {}
```

```typescript
// app.component.ts
import { Component } from '@angular/core';
import 'overrep-form';

@Component({
  selector: 'app-root',
  template: `
    <overrep-form
      [ontologyOptions]="ontologyOptions"
      [exampleGenes]="exampleGenes"
      submitUrl="/api/overrep"
    ></overrep-form>
  `
})
export class AppComponent {
  ontologyOptions = [
    { id: "biological_process_IBA", label: "biological process PAN-GO" },
    { id: "molecular_function_IBA", label: "molecular function PAN-GO" },
    { id: "cellular_component_IBA", label: "cellular component PAN-GO" }
  ];

  exampleGenes = [
    "AKT1", "BDNF", "CCKAR", "CHI3L1", "CHRNA7",
    "CLDN5", "CNR1", "COMT"
  ];
}
```

## Props

| Prop              | Type               | Default                      | Description                           |
| ----------------- | ------------------ | ---------------------------- | ------------------------------------- |
| `ontologyOptions` | `OntologyOption[]` | `[]`                         | Array of available ontology options   |
| `exampleGenes`    | `string[]`         | `[]`                         | Example gene IDs to populate the form |
| `submitUrl`       | `string`           | `/api/overrep`               | URL for form submission               |
| `species`         | `string`           | `'HUMAN'`                    | Species identifier                    |
| `testType`        | `string`           | `'FISHER'`                   | Statistical test type                 |
| `textareaRows`    | `number`           | `3`                          | Number of rows in gene ID textarea    |
| `submitLabel`     | `string`           | `'Launch'`                   | Submit button label                   |
| `examplesLabel`   | `string`           | `'Examples'`                 | Examples button label                 |
| `geneIdsLabel`    | `string`           | `'Your Gene IDs'`            | Gene IDs input label                  |
| `ontologyLabel`   | `string`           | `'Ontology'`                 | Ontology selector label               |
| `hint`            | `string`           | `'can use UniProt ID/AC...'` | Help text shown below form            |
| `showHint`        | `boolean`          | `true`                       | Toggle hint visibility                |

## Events

The component emits a single event `overrepSubmit` when the form is submitted:

```typescript
interface FormSubmitEvent {
  geneIds: string;    // Newline-separated gene IDs
  ontology: string;   // Selected ontology ID
  species: string;    // Species identifier
  testType: string;   // Statistical test type
}
```

## Development

1. Clone the repository

```bash
git clone [will-change-repo]
```

2. Install dependencies

```bash
npm install
```

3. Start development server

```bash
npm start
```

4. Running Tests

```bash
npm test
```

5. Build for production

```bash
npm run build
```

## Browser Support

- Chrome 67+
- Firefox 63+
- Safari 10.1+
- Edge 79+

## License

MIT

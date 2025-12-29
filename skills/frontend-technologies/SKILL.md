---
name: frontend-technologies
description: Master modern frontend technologies including React, Vue, Angular, TypeScript, Next.js, CSS architecture, and responsive design. Use when working with frontend frameworks, styling, or browser APIs.
sasmp_version: "1.3.0"
bonded_agent: 01-frontend-web-development
bond_type: PRIMARY_BOND
---

# Frontend Technologies

## Quick Start

### React Basics
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
```

### Vue 3 Composition API
```javascript
import { ref } from 'vue';

export default {
  setup() {
    const count = ref(0);

    return {
      count,
      increment: () => count.value++
    };
  }
};
```

### TypeScript with React
```typescript
interface Props {
  message: string;
  onSubmit: (value: string) => void;
}

const MyComponent: React.FC<Props> = ({ message, onSubmit }) => {
  return <div onClick={() => onSubmit(message)}>{message}</div>;
};
```

## Core Frameworks

### React Ecosystem
- **Hooks**: useState, useEffect, useContext, useReducer, useCallback, useMemo
- **State Management**: Redux, Zustand, Jotai, Recoil
- **Server Frameworks**: Next.js with App Router and Server Components
- **Form Libraries**: React Hook Form, Formik
- **Testing**: Jest, React Testing Library, Cypress, Playwright
- **Build Tools**: Vite, Webpack, Turbopack

### Vue.js Specialization
- **Composition API**: Advanced reactivity and composables
- **Component Patterns**: Scoped slots, render functions, renderless components
- **State Management**: Pinia (modern Vuex alternative)
- **Routing**: Vue Router 4 with nested routes
- **Meta Frameworks**: Nuxt for SSR and static generation
- **Build Optimization**: Vite for rapid development

### Angular Enterprise Development
- **Dependency Injection**: Services, providers, tokens
- **RxJS**: Observables, operators, subjects
- **Forms**: Reactive forms with FormBuilder
- **HTTP Client**: Interceptors and error handling
- **Testing**: Jasmine, Karma, Jest
- **Modules**: Feature modules, shared modules, lazy loading

## Modern CSS

### CSS Architecture
```css
/* BEM Naming Convention */
.card { }
.card__header { }
.card__header--highlighted { }

/* CSS Variables */
:root {
  --primary-color: #007bff;
  --spacing-unit: 8px;
}

.button {
  background: var(--primary-color);
  padding: calc(var(--spacing-unit) * 2);
}
```

### Advanced Techniques
- **Flexbox & Grid**: Advanced layouts, subgrid, alignment
- **CSS-in-JS**: Styled Components, Emotion, Tailwind
- **Animation**: Transitions, keyframes, animation libraries
- **Responsive Design**: Mobile-first, fluid typography, container queries
- **Performance**: Critical CSS, CSS loading optimization
- **Accessibility**: Color contrast, focus states, ARIA attributes

## Component Architecture

### Design Patterns
- **Presentational/Container Components**: Separation of concerns
- **Compound Components**: Complex component interactions
- **Render Props**: Component logic reuse
- **Custom Hooks**: Encapsulated component logic
- **Higher-Order Components**: Wrapper patterns
- **Slots**: Flexible component composition

### Component Libraries
- **Material-UI**: Enterprise component system
- **Chakra UI**: Accessible component library
- **Headless UI**: Unstyled accessible components
- **Storybook**: Component documentation and testing

## TypeScript Mastery

### Advanced Types
```typescript
// Union and Intersection Types
type Success = { status: 'success'; data: unknown };
type Error = { status: 'error'; message: string };
type Result = Success | Error;

// Generics
function process<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

// Conditional Types
type Flatten<T> = T extends Array<infer U> ? U : T;

// Utility Types
type Partial<T> = { [K in keyof T]?: T[K] };
type Readonly<T> = { readonly [K in keyof T]: T[K] };
```

## Performance Optimization

### Techniques
- **Code Splitting**: Route-based and component-based splitting
- **Lazy Loading**: React.lazy, dynamic imports
- **Memoization**: React.memo, useMemo, useCallback
- **Bundle Analysis**: webpack-bundle-analyzer
- **Image Optimization**: Next.js Image, WebP, responsive images
- **Core Web Vitals**: LCP, FID, CLS optimization

## Resources

- **React Docs**: https://react.dev
- **Vue Docs**: https://vuejs.org
- **Angular Docs**: https://angular.io
- **TypeScript Handbook**: https://www.typescriptlang.org/docs/
- **MDN Web Docs**: https://developer.mozilla.org
- **Web Fundamentals**: https://web.dev

---

**See Also**: design-system, responsive-design-patterns

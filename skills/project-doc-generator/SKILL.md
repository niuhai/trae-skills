***

name: project-doc-generator
description: Performs comprehensive code scanning and generates professional, structured technical documentation. Invoke when user asks to generate project documentation or create docs for a codebase.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Project Documentation Generator

## Functionality

Performs comprehensive code scanning on a project to generate professional, complete, and structured technical documentation. Documentation is strictly based on source code scanning results, ensuring strict consistency between documentation and code implementation.

## Core Principles

1. **Scan First** - All documentation content must be based on actual code scanning, no fabrication
2. **Layered Organization** - Documentation organized by infrastructure layer → business module layer → common module layer
3. **Atomic** - Each business module is an independent md file
4. **Visualization** - Use ASCII diagrams to showcase architecture and processes

***

## Phase 1: Project Scanning

### 1.1 Basic Structure Scanning

```bash
# Scan project root directory
LS {project_path}

# Get source files
Glob {project_path}/src/**/*.ts
Glob {project_path}/src/**/*.vue
Glob {project_path}/src/**/*.json
```

### 1.2 Configuration File Scanning

Must read the following files:

- `package.json` - Dependencies and tech stack
- `vite.config.ts` - Build configuration
- `tsconfig.json` - TypeScript configuration
- `.eslintrc.js` - Code standards
- `.env*` - Environment variable configuration

### 1.3 Business Module Scanning

Scan in the following directory order:

```
src/
├── api/                    # API interface layer
├── views/                  # Page view layer
├── components/             # Common components
├── store/                  # State management
├── router/                 # Route configuration
├── utils/                  # Utility functions
└── enum/                   # Enum definitions
```

***

## Phase 2: Documentation Structure Planning

### 2.1 Directory Structure Template

```
{project_path}/项目文档/
├── 01-项目概述/
│   └── 项目概述.md
├── 02-技术架构/
│   └── 技术架构.md
├── 03-{业务模块A}/
│   └── {业务模块A}.md
├── 04-{业务模块B}/
│   └── {业务模块B}.md
├── ...
├── 0N-{最后业务模块}/
│   └── {最后业务模块}.md
├── 0N+1-API接口规范/
│   └── API接口规范.md
├── 0N+2-数据模型/
│   └── 数据模型.md
├── 0N+3-核心业务逻辑/
│   └── 核心业务逻辑.md
└── 0N+4-部署配置/
    └── 部署配置.md
```

### 2.2 Business Module Identification Rules

- Each first-level directory under `src/views/` = one business module
- Module names use Chinese, format: `{sequence}-{Module Chinese Name}`
- Special cases: modules with multiple sub-tools need further subdivision (e.g., small tools management divided into 8 sub-modules by function)

***

## Phase 3: Documentation Templates

### 3.1 Project Overview Template

```markdown
# {Project Name} - Project Overview

## 1.1 Project Background

- **Project Name**:
- **Project Code**:
- **Company**:
- **Project Nature**:

## 1.2 Project Objectives

Provide...for..., including:

- {Objective 1} - {Description}
- {Objective 2} - {Description}

## 1.3 System Architecture Diagram

Use ASCII to draw system architecture diagram showing:
- Frontend tech stack
- Layer structure
- Backend interaction

```

{ASCII Architecture Diagram}

```

## 1.4 Project Tech Stack

| Category | Technology | Version |
|------|------|------|
| Framework | {Framework} | {Version} |
| Language | {Language} | {Version} |
| ... | ... | ... |

## 1.5 Project Version Requirements

- Node.js: {Version}
- npm: {Version}
- {Other}: {Version}
```

### 3.2 Technical Architecture Template

```markdown
# Technical Architecture

## 2.1 Project Directory Structure

Use ASCII tree structure to display complete directory:

```

src/
├── api/                    # {Description}
├── views/                  # {Description}
├── components/             # {Description}
├── store/                 # {Description}
├── router/                # {Description}
├── utils/                 # {Description}
└── enum/                  # {Description}

```

## 2.2 Technical Architecture Layer Diagram

Use ASCII to draw layered architecture diagram:

```

{Layered Architecture Diagram}

```
```

### 3.3 Business Module Template

````markdown
# {Module Name}

## Module Introduction

**Function Description:** {Function Description}

**Source Code Path:** `src/views/{Module Path}/`

## Page Description

| Page | File Path | Function Description |
|------|---------|---------|
| {PageName}.vue | src/views/{path}/{PageName}.vue | {Function} |

## Component Description

| Component Name | File Path | Function Description |
|---------|---------|---------|
| {ComponentName}.vue | src/views/{path}/components/{ComponentName}.vue | {Function} |

## Core Functions

| Function | Description |
|-----|------|
| {Function 1} | {Description} |
| {Function 2} | {Description} |

## Core Interfaces

| Interface Path | Function Description |
|---------|---------|
| /{module}/{action} | {Description} |

## {Status Enum Name} ({Enum Key})

Use code block to display complete enum definition:

```typescript
const {ENUM_KEY} = {
  {KEY1}: "{Value1}",           // {Color class}
  {KEY2}: "{Value2}",          // {Color class}
};
````

## {Business Process Name} Diagram

Use ASCII to draw flowchart:

```
{Flowchart}
```

````

### 3.4 API Interface Specification Template

```markdown
# API Interface Specification

## HTTP Request封装 ({file})

```typescript
export default {
  get(url: string, params?: object)      // {Description}
  post(url: string, data?: object)      // {Description}
  postJson(url: string, data?: object)   // {Description}
  // ...
}
````

## Request Interceptor ({file})

**Request Interceptor Functions:**

- {Function 1}
- {Function 2}

```typescript
{Interceptor Core Code}
```

## Authentication Mechanism

**Login Flow:**

```
{Login Flowchart}
```

**RSA Encryption Implementation ({file}):**

```typescript
{RSA Encryption Code}
```

## Unified Response Format

```typescript
interface ResType {
  data: any;
  code: number;    // {Description}
  message: string;
}
```

## Interface Path Specification

| Prefix    | Module Description |
| --------- | ------------------ |
| /{prefix} | {Description}      |

````

### 3.5 Data Model Template

```markdown
# Data Model

## Core Type Definitions

### {TypeName} ({file})

```typescript
interface {TypeName} {
  {field1}: {type};    // {Description}
  {field2}?: {type};   // {Description}
}
````

## Status Enum Definitions

### {Enum Name}

| Status Value | Display Name | Color Class |
| ------------ | ------------ | ----------- |
| {KEY1}       | {Value1}     | {class}     |
| {KEY2}       | {Value2}     | {class}     |

````

### 3.6 Core Business Logic Template

```markdown
# Core Business Logic

## {Business Logic Name} ({file})

### Flowchart

````

{Flowchart}

````

### Core Code

```typescript
{Core Code}
````

````

### 3.7 Deployment Configuration Template

```markdown
# Deployment Configuration

## Environment Variable Configuration

### {Environment Name} (.env.{env})

````

{Environment Variable Content}

````

| Variable Name | Description |
|--------|------|
| {VAR_NAME} | {Description} |

## Build Commands

| Command | Description |
|------|------|
| `{command}` | {Description} |

## Nginx Configuration

```nginx
{nginx configuration}
````

```

---

## Phase 4: Visualization Elements

### 4.1 System Architecture Diagram Template

```

┌─────────────────────────────────────────────────────────────┐
│                        {Tech Stack Name}                      │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │
│  │  {Layer 1}  │  │  {Layer 1}  │  │  {Layer 1}  │          │
│  │  ({Tech})   │  │  ({Tech})   │  │  ({Tech})   │          │
│  └─────────────┘  └─────────────┘  └─────────────┘          │
├─────────────────────────────────────────────────────────────┤
│  ┌───────────────────────────────────────────────────────┐  │
│  │              {Layer 2 Name} ({Tech})                    │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘

```

### 4.2 Flowchart Template

```

┌──────┐     ┌──────────────┐     ┌───────────┐
│ {State A}│────▶│   {State B}    │────▶│  {State C}  │
└──┬───┘     └──────────────┘     └─────┬─────┘
│                                      │
│           ┌───────────┐              │
│           │   {State D} │◀─────────────┘
│           └───────────┘

```

### 4.3 Layered Architecture Diagram Template

```

┌─────────────────────────────────────────────────────────────┐
│                    {Architecture Name}                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │                    {Layer 1 Name}                     │   │
│  │    {Component 1}/  {Component 2}/  {Component 3}    │   │
│  └─────────────────────────────────────────────────────┘   │
│                              │                              │
│                              ▼                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │                    {Layer 2 Name}                     │   │
│  │         {Module A} │ {Module B} │ {Module C}        │   │
│  └─────────────────────────────────────────────────────┘   │
│                              │                              │
│                              ▼                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │                    {Layer 3 Name}                     │   │
│  │              {Tech 1} │ {Tech 2} │ {Tech 3}        │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘

````

---

## Phase 5: Execution Process

### Step 1: Scan Project

1. `LS {project_path}` - View project structure
2. `Glob **/*.vue` - Get all Vue components
3. `Glob **/*.ts` - Get all TypeScript files
4. Read configuration files (package.json, vite.config.ts, etc.)

### Step 2: Analyze Modules

1. Scan `src/views/` to determine business module quantity and names
2. Scan `src/api/` to determine interface structure
3. Scan `src/enum/` to determine enum definitions
4. Scan `src/store/` to determine state management

### Step 3: Create Directories

```bash
mkdir "项目文档/01-项目概述"
mkdir "项目文档/02-技术架构"
mkdir "项目文档/03-{Module 1}"
# ... Create based on actual business modules
mkdir "项目文档/0N-API接口规范"
mkdir "项目文档/0N+1-数据模型"
mkdir "项目文档/0N+2-核心业务逻辑"
mkdir "项目文档/0N+3-部署配置"
````

### Step 4: Generate Documentation

Use sub-agents to generate module documentation in parallel:

- Each module is an independent md file
- Strictly follow template structure
- Include ASCII diagrams
- Based on actual scanned code

***

## Quality Standards

1. **Accuracy** - Documentation content must be strictly consistent with code
2. **Completeness** - Each module must include: introduction, pages, components, interfaces, enums, flowcharts
3. **Readability** - Precise language, clear logic, reasonable structure
4. **Visualization** - Key processes must include ASCII diagrams

***

## Output

Generate in `{project_path}/项目文档/` directory:

1. **项目概述.md** - Project background, tech stack, architecture diagram
2. **技术架构.md** - Directory structure, architecture layering
3. **{Business Module N}.md** - Detailed documentation for each business module
4. **API接口规范.md** - HTTP封装, interceptors, authentication
5. **数据模型.md** - Type definitions, enums
6. **核心业务逻辑.md** - Core algorithms, processes
7. **部署配置.md** - Environment variables, build commands


# Macro_Tree

> [!NOTE]
> This project is currently under active architectural refactoring.  
> The codebase and documentation are being updated for clarity, modularity, and maintainability.

A tree-based macro management application designed to improve productivity and automation.  
Inspired by a professional automation tool, this project removes security-related elements and focuses on extensibility and flexibility.

*Read this in other languages: [한국어](README_KR.md)*

---

## Project Status

- ✅ **Core Module**: Complete (interface design, core implementations)
- ✅ **Model Layer**: Complete (repository, file, db, state management)
- 🔄 **ViewModel / View**: In progress (import path, naming, responsibility, pattern unification)
- 🧪 **Test/Docs/Automation**: Planned

---

## Key Features

- Tree node movement, insertion, and deletion
- Undo/Redo functionality
- Mouse coordinate acquisition
- Grouping and instance creation
- Data persistence (save/load)
- Hierarchical structure visualization and manipulation

---

## Architecture

- **SOLID Principles**: SRP, OCP, LSP, ISP, DIP
- **Interface-based Design**: Protocols for clear contracts
- **Layered Architecture**: Core, Model, ViewModel, View, Platforms

### Layer Overview

- **core/**: Core business logic, interfaces, and implementations
- **model/**: Business logic extension (repositories, services, state, events)
- **viewmodel/**: ViewModel layer (state transformation, UI logic)
- **view/**: View layer (PyQt6/QML UI components)
- **platforms/**: Platform-specific adapters
- **test/**: Test code

<details>
<summary>Project Structure</summary>

```
├── core/                     # Core business logic
│   ├── interfaces/           # Core interfaces
│   └── impl/                 # Core implementations
├── model/                    # Business logic extension layer
│   ├── store/                # Data persistence (repo, file, db)
│   │   ├── repo/             # Repository interfaces
│   │   ├── file/             # File-based repo implementation
│   │   └── db/               # DB-based repo implementation
│   ├── services/             # Business services
│   ├── action/               # Action handling
│   └── events/               # Event handling
├── viewmodel/                # ViewModel layer
├── view/                     # View layer
├── platforms/                # Platform-specific code
└── test/                     # Test code
```
</details>

![Architecture Diagram](images/architecture.png)

## Interface Structure

- **Core Interfaces:** Basic interfaces for tree and item components
- **Model Interfaces:** Business logic interfaces (repository, state manager)
- **Implementation Classes:** Concrete implementations of interfaces
- **TreeStateManager:** Manages and tracks tree state
- **TreeRepository:** Handles data persistence operations
- **MTTreeViewModel:** Presentation logic for tree data
- **TreeView:** User interface component

## Tech Stack

- **Backend**: Python 3.10
- **Frontend**: PyQt6, QML
- **Data Management**: PostgreSQL, File-based storage
- **Architecture**: MVVM pattern, Protocol-based interfaces
- **Automation**: PyAutoGUI, pynput

## Design Principles & Patterns

### Protocol-based Interface Design
- **Structural Typing**: Interface compliance without explicit inheritance
- **Static Type Checking Support**: Enhanced stability through mypy

### MVVM Architecture Pattern
- **Separation of Concerns**: UI and business logic separation
- **Testability**: Independent testing of ViewModels

### Dependency Inversion
- **High-level Policy Protection**: Core module not dependent on concrete implementations
- **Enhanced Extensibility**: Minimal code changes when adding new features

### Observer Pattern for State Change Notification
- **Decoupled Communication**: The ViewModel, StateManager, and EventManager utilize an observer (subscribe/notify) structure, allowing state changes to be communicated without direct coupling to the UI (View).
- **Reactive UI**: Subscribers (such as the UI) are automatically updated whenever the underlying data changes, enabling a responsive and dynamic interface.

### Repository Pattern for Data Access Abstraction
- **Persistence Layer Isolation**: Data access logic (such as saving/loading trees to DB or files) is abstracted from business logic via repository interfaces.
- **Flexibility**: The system can be easily extended or switched between different storage backends (e.g., PostgreSQL, file) by implementing the repository interface.

### State Pattern for Undo/Redo Management (Leveraging State Manager)
- **Encapsulated State Transitions**: The StateManager manages the tree's state history, providing robust Undo/Redo functionality.
- **Simplified ViewModel**: The ViewModel delegates state management (history, restoration, etc.) to the StateManager, resulting in cleaner and more maintainable code.

## Code Quality and Standards

- **Coding Style Guide**: The project follows the coding style rules defined in `CODING_STYLE.md` for consistency.
- **Linters and Formatters**: `flake8` (for linting) and `isort` (for import sorting, configured in `setup.cfg`) are used to maintain code quality.
- **Static Type Checking**: Type hints are used throughout the codebase, and `mypy` (configured in `mypy.ini`) is employed for static type analysis to enhance code reliability and maintainability.

## Demo

This project is currently under architectural refactoring. By portfolio submission, a minimal functional demo will be provided with the following features:

- Tree node creation, editing, and deletion
- Basic macro setup and management
- Simple UI visualization

## Demo Video

![main](https://user-images.githubusercontent.com/110750614/211150674-dfd5aa99-2ea1-47f3-839d-2494f83ab985.gif)
(This is a demo video based on legacy code.)

## Requirements
- Python 3.10 or higher
- PostgreSQL (for data persistence)
- Windows operating system

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
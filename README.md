# Finite State Machine (FSM) Framework

A lightweight and modular state machine implementation designed for Unity projects, providing a clean structure for game state management.

## Core Architecture

### Interfaces
- **IState**: Defines the fundamental state contract with `EnterState()`, `ExitState()`, and `UpdateState()` methods.
- **IStateActivator**: Interface for state transition control, including activation, deactivation, and updates.
- **ILogger**: Abstraction for logging with support for standard, warning, and error messages.

### Key Components
- **StateRegistry**: Central repository for state instances, enabling type-based lookup and registration.
- **StateActivator**: Manages state lifecycle (activation/deactivation) and ensures proper transitions between states.
- **BaseFinalStateMachine**: Core abstract class handling state switching, registry access, and logging (with a built-in `NullLogger`).
- **FinalStateMachine**: Concrete implementation exposing a simplified API for state transitions.
- **BaseFinalStateMachineBuilder**: Implements the Builder pattern for fluent and type-safe FSM construction.

### Features
- **Type-Safe State Management**: States are registered and retrieved by their exact type.
- **Automatic State Cleanup**: Handles proper deactivation of previous states during transitions.
- **Optional Logging**: Supports custom loggers or silent operation via the `NullLogger` default.
- **Update Propagation**: Built-in support for per-frame state updates via `UpdateStates()`.
- **Fluent Builder API**: Simplifies FSM setup and state registration.

## Design Principles
1. **Separation of Concerns**: Clear division between state storage (Registry), lifecycle (Activator), and machine logic.
2. **Extensibility**: Interfaces allow custom implementations of logging, state handling, etc.
3. **Null Safety**: Graceful handling of missing states with error logging.
4. **No MonoBehaviour Coupling**: Core logic is Unity-agnostic (except for the `NullLogger` location).

## Integration
1. Implement `IState` for your game states.
2. Use the `Builder` to register states and instantiate the FSM.
3. Control states via `SwitchToState<TState>()` and regular `UpdateStates()` calls.

> Note: Requires Unity's .NET runtime due to `UnityEngine` dependency in `BaseFinalStateMachine.cs`.

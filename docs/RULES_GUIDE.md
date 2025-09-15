# Agent Rules Guide

This guide explains how to create, structure, and maintain `.rules` files for AI IDE integrations. Follow these best practices to ensure your rules are effective, consistent, and compatible across environments.

## What Are `.rules` Files?

`.rules` files define project-specific instructions, coding standards, and context for AI-powered code generation and understanding.

## Anatomy of a Rule

A robust `.rules` file typically includes the following sections:

- **name**: Unique identifier for the rule
- **description**: Brief summary of what the rule enforces
- **filters**: Criteria for targeting files or code (e.g., file extensions, content patterns)
- **actions**: What happens when the rule matches (e.g., suggest improvements, enforce changes)
- **examples**: Before/after code samples to clarify intent
- **metadata**: Priority, version, tags, and other organizational info

## Writing Rules

- Use clear, concise language
- Structure rules using YAML for complex logic, JSON for simple cases
- Document the purpose and scope of each rule
- Include actionable suggestions and educational context
- Provide before/after code examples

## Filtering Strategies

Filters allow you to target specific files or code constructs:

- **file_extension**: Apply rules to certain file types (e.g., `.ts`, `.js`)
- **content**: Use regex patterns to match code structures (e.g., classes, interfaces, functions)

Example:
```yaml
filters:
  - type: file_extension
    pattern: "\\.ts$|\\.js$"
  - type: content
    pattern: "(?s)class.*?\\{|interface.*?\\{|function.*?\\{"
```

## Validating Rules

- Test rules in supported IDEs
- Ensure schema compliance
- Check for conflicts with existing rules
- Use sample inputs to verify expected suggestions or enforcement

## Actions

Actions define what happens when a rule matches:

- **suggest**: Provide guidance, best practices, or code improvements
- **enforce**: Require changes or block undesired patterns
- **message**: Use multi-line, markdown-formatted messages for clarity

Example:
```yaml
actions:
  - type: suggest
    message: |
      When writing code, follow these SOLID principles:
      1. Single Responsibility Principle (SRP)
      2. Open/Closed Principle (OCP)
      3. Liskov Substitution Principle (LSP)
      4. Interface Segregation Principle (ISP)
      5. Dependency Inversion Principle (DIP)
```

## Best Practices

- Keep rules atomic and focused
- Maintain cross-platform compatibility
- Update documentation for any new or changed rules
- Use metadata for organization and discoverability
- Prefer composition and modularity in rule design

## Example Rule

### Simple JSON Example

```json
{
  "name": "no-console-log",
  "description": "Disallow use of console.log in production code",
  "severity": "error",
  "pattern": "console\\.log"
}
```

### Advanced YAML Example: SOLID Principles

```yaml
name: solid_principles
description: Enforces SOLID principles in code design and implementation
filters:
  - type: file_extension
    pattern: "\\.ts$|\\.js$"
  - type: content
    pattern: "(?s)class.*?\\{|interface.*?\\{|function.*?\\{"

actions:
  - type: suggest
    message: |
      When writing code, follow these SOLID principles:

      1. Single Responsibility Principle (SRP):
         - Each class/module should have only one reason to change
         - Keep classes focused and cohesive
         - Extract separate concerns into their own classes
         Example:
         ```typescript
         // Good: Single responsibility
         class UserAuthentication {
           authenticate(credentials: Credentials): boolean { ... }
         }
         class UserProfile {
           updateProfile(data: ProfileData): void { ... }
         }

         // Bad: Multiple responsibilities
         class User {
           authenticate(credentials: Credentials): boolean { ... }
           updateProfile(data: ProfileData): void { ... }
           sendEmail(message: string): void { ... }
         }
         ```

      2. Open/Closed Principle (OCP):
         - Classes should be open for extension but closed for modification
         - Use interfaces and abstract classes
         - Implement new functionality through inheritance/composition
         Example:
         ```typescript
         // Good: Open for extension
         interface PaymentProcessor {
           process(payment: Payment): void;
         }
         class CreditCardProcessor implements PaymentProcessor { ... }
         class PayPalProcessor implements PaymentProcessor { ... }

         // Bad: Closed for extension
         class PaymentProcessor {
           process(payment: Payment, type: string): void {
             if (type === 'credit') { ... }
             else if (type === 'paypal') { ... }
           }
         }
         ```

      3. Liskov Substitution Principle (LSP):
         - Derived classes must be substitutable for their base classes
         - Maintain expected behavior when using inheritance
         - Don't violate base class contracts
         Example:
         ```typescript
         // Good: Derived class maintains base contract
         class Bird {
           fly(): void { ... }
         }
         class Sparrow extends Bird {
           fly(): void { ... } // Implements flying behavior
         }

         // Bad: Violates base contract
         class Penguin extends Bird {
           fly(): void {
             throw new Error("Can't fly!"); // Violates base class contract
           }
         }
         ```

      4. Interface Segregation Principle (ISP):
         - Don't force clients to depend on interfaces they don't use
         - Keep interfaces small and focused
         - Split large interfaces into smaller ones
         Example:
         ```typescript
         // Good: Segregated interfaces
         interface Readable {
           read(): void;
         }
         interface Writable {
           write(data: string): void;
         }

         // Bad: Fat interface
         interface FileSystem {
           read(): void;
           write(data: string): void;
           delete(): void;
           create(): void;
           modify(): void;
         }
         ```

      5. Dependency Inversion Principle (DIP):
         - High-level modules shouldn't depend on low-level modules
         - Both should depend on abstractions
         - Use dependency injection
         Example:
         ```typescript
         // Good: Depends on abstraction
         interface Logger {
           log(message: string): void;
         }
         class UserService {
           constructor(private logger: Logger) {}
         }

         // Bad: Depends on concrete implementation
         class UserService {
           private logger = new FileLogger();
         }
         ```

      Additional Guidelines:
      - Use interfaces to define contracts
      - Implement dependency injection
      - Keep classes small and focused
      - Use composition over inheritance when possible
      - Write unit tests to verify SOLID compliance

examples:
  - input: |
      // Bad example - violates SRP and OCP
      class OrderProcessor {
        processOrder(order: Order) {
          // Handles validation
          // Handles payment
          // Handles shipping
          // Handles notification
        }
      }
    output: |
      // Good example - follows SOLID principles
      interface OrderValidator {
        validate(order: Order): boolean;
      }
      interface PaymentProcessor {
        process(order: Order): void;
      }
      interface ShippingService {
        ship(order: Order): void;
      }
      interface NotificationService {
        notify(order: Order): void;
      }

      class OrderProcessor {
        constructor(
          private validator: OrderValidator,
          private paymentProcessor: PaymentProcessor,
          private shippingService: ShippingService,
          private notificationService: NotificationService
        ) {}

        processOrder(order: Order) {
          if (this.validator.validate(order)) {
            this.paymentProcessor.process(order);
            this.shippingService.ship(order);
            this.notificationService.notify(order);
          }
        }
      }

metadata:
  priority: high
  version: 1.0
  tags:
    - code-quality
    - design-patterns
    - best-practices
```

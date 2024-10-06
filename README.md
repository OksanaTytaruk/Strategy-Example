# Strategy Example

Цей репозиторій містить приклад патерну проектування "Стратегія".

## Патерн Стратегія (Strategy)

Патерн "Стратегія" визначає сімейство алгоритмів, інкапсулює кожен з них і робить їх взаємозамінними. Патерн дозволяє алгоритмам варіюватися незалежно від клієнтів, які їх використовують.

### Приклад коду:

```csharp
using System;

// Стратегія
public interface IStrategy
{
    void Execute();
}

// Конкретні стратегії
public class ConcreteStrategyA : IStrategy
{
    public void Execute()
    {
        Console.WriteLine("Виконання стратегії A");
    }
}

public class ConcreteStrategyB : IStrategy
{
    public void Execute()
    {
        Console.WriteLine("Виконання стратегії B");
    }
}

// Контекст
public class Context
{
    private IStrategy _strategy;

    public Context(IStrategy strategy)
    {
        _strategy = strategy;
    }

    public void SetStrategy(IStrategy strategy)
    {
        _strategy = strategy;
    }

    public void ExecuteStrategy()
    {
        _strategy.Execute();
    }
}

class Program
{
    static void Main(string[] args)
    {
        Context context = new Context(new ConcreteStrategyA());
        
        context.ExecuteStrategy(); // Виконання стратегії A

        context.SetStrategy(new ConcreteStrategyB());
        context.ExecuteStrategy(); // Виконання стратегії B
    }
}

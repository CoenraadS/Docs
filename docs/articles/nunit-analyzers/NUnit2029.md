# NUnit2029

## Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)

| Topic    | Value
| :--      | :--
| Id       | NUnit2029
| Severity | Info
| Enabled  | True
| Category | Assertion
| Code     | [ClassicModelAssertUsageAnalyzer](https://github.com/nunit/nunit.analyzers/blob/3.8.0/src/nunit.analyzers/ClassicModelAssertUsage/ClassicModelAssertUsageAnalyzer.cs)

## Description

Consider using the constraint model, `Assert.That(actual, Is.LessThan(expected))`, instead of the classic model, `Assert.Less(actual, expected)`.

## Motivation

The assert `Assert.Less` from the classic Assert model makes it easy to confuse the `expected` and the `actual` argument,
so this analyzer marks usages of `Assert.Less`.

```csharp
[Test]
public void Test()
{
    Assert.Less(actual, expected);
}
```

## How to fix violations

The analyzer comes with a code fix that will replace `Assert.Less(actual, expected)` with
`Assert.That(actual, Is.LessThan(expected))`. So the code block above will be changed into.

```csharp
[Test]
public void Test()
{
    Assert.That(actual, Is.LessThan(expected));
}
```

<!-- start generated config severity -->
## Configure severity

### Via ruleset file

Configure the severity per project, for more info see [MSDN](https://learn.microsoft.com/en-us/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules?view=vs-2022).

### Via .editorconfig file

```ini
# NUnit2029: Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)
dotnet_diagnostic.NUnit2029.severity = chosenSeverity
```

where `chosenSeverity` can be one of `none`, `silent`, `suggestion`, `warning`, or `error`.

### Via #pragma directive

```csharp
#pragma warning disable NUnit2029 // Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)
Code violating the rule here
#pragma warning restore NUnit2029 // Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)
```

Or put this at the top of the file to disable all instances.

```csharp
#pragma warning disable NUnit2029 // Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)
```

### Via attribute `[SuppressMessage]`

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Assertion",
    "NUnit2029:Consider using Assert.That(actual, Is.LessThan(expected)) instead of Assert.Less(actual, expected)",
    Justification = "Reason...")]
```
<!-- end generated config severity -->

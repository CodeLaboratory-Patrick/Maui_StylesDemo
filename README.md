# Styles in .NET MAUI

## Overview of Implicit Styles
**Implicit Styles** in **.NET MAUI** provide a powerful way to define and apply consistent styling to UI elements across an application. Unlike **explicit styles**, which are applied by specifying a style key, **implicit styles** are automatically applied to all elements of the specified type without needing to reference them explicitly.

Implicit styles are useful for creating a unified look and feel for an application, reducing the amount of repetitive code required for styling, and enhancing the maintainability of UI elements.

## Key Features
- **Automatic Application**: Implicit styles are automatically applied to all instances of a particular type, such as `Button` or `Label`, throughout the application or within a specific scope.
- **Global Styling**: When defined in **App.xaml**, implicit styles can be used to set global design standards for all pages in the application.
- **Override Mechanism**: You can still override implicit styles on individual controls by defining explicit styles.

### Implicit Styles vs. Explicit Styles
| Feature                      | Implicit Styles                            | Explicit Styles                           |
|------------------------------|--------------------------------------------|-------------------------------------------|
| **Application**              | Automatically applied to elements         | Applied explicitly using a `Style` key    |
| **Ease of Use**              | Simple to use; no need to reference styles | Requires explicit reference               |
| **Override Capability**      | Can be overridden by explicit styles       | Must be applied explicitly                |

## Example of Implicit Styles
Here's an example of how to use implicit styles in a .NET MAUI application.

### App.xaml Example
Define a global implicit style for `Button` and `Label` controls in `App.xaml`:

```xml
<Application xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.App">
    <Application.Resources>
        <ResourceDictionary>
            <!-- Implicit Style for Button -->
            <Style TargetType="Button">
                <Setter Property="BackgroundColor" Value="LightBlue" />
                <Setter Property="TextColor" Value="White" />
                <Setter Property="FontAttributes" Value="Bold" />
                <Setter Property="CornerRadius" Value="10" />
            </Style>

            <!-- Implicit Style for Label -->
            <Style TargetType="Label">
                <Setter Property="TextColor" Value="DarkSlateGray" />
                <Setter Property="FontSize" Value="18" />
                <Setter Property="HorizontalOptions" Value="Center" />
            </Style>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```
### Explanation
- **Application.Resources**: The `ResourceDictionary` defines the styles that are available throughout the entire application.
- **TargetType**: Specifies the type of control to which the style will be applied (e.g., `Button` or `Label`).
- **Setters**: Define properties for the target control, such as `BackgroundColor`, `TextColor`, and `FontSize`. These properties will be automatically applied to all buttons and labels throughout the application.

### Page-Level Example
Implicit styles can also be defined at the page level if you only want to style elements on a specific page. For example, within a `ContentPage`:

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.MainPage">
    <ContentPage.Resources>
        <ResourceDictionary>
            <Style TargetType="Entry">
                <Setter Property="PlaceholderColor" Value="Gray" />
                <Setter Property="TextColor" Value="Black" />
                <Setter Property="FontSize" Value="16" />
            </Style>
        </ResourceDictionary>
    </ContentPage.Resources>
    
    <StackLayout Padding="20">
        <Entry Placeholder="Enter text here..." />
        <Entry Placeholder="Another entry..." />
    </StackLayout>
</ContentPage>
```
- In this example, every `Entry` element on the page will automatically receive the defined style, without requiring explicit style assignment.

## Practical Use Cases
### When to Use Implicit Styles
- **Consistent Design**: When you need a consistent look and feel for controls throughout the app, such as buttons with the same colors and font settings.
- **Maintainability**: When you want to minimize the need to specify the same style attributes repeatedly, making the code easier to maintain and update.
- **Application-Wide Theming**: When you want to create themes that can be applied throughout the entire application by modifying just one location (e.g., `App.xaml`).

### Example Scenarios
- **Form Design**: Creating implicit styles for `Entry` fields and `Button` controls so that all forms in the app have a consistent design.
- **Theming**: Defining styles in `App.xaml` to apply a particular theme across all pages in the app. For example, having all buttons with a rounded corner and specific color scheme.
- **Responsive Design**: Applying consistent padding, margins, or alignment properties to ensure UI elements are positioned correctly on various screen sizes.

## Summary Table of Key Elements
| Component                      | Description                                      |
|--------------------------------|--------------------------------------------------|
| **Implicit Style**             | Style applied to all controls of a specific type without explicit reference. |
| **Application.Resources**      | Defines styles globally for the entire application. |
| **TargetType**                 | Specifies the type of control the style applies to (e.g., `Button`). |
| **Setters**                    | Defines the property values for the styled controls (e.g., `TextColor`, `FontSize`). |

## Reference Sites
- [.NET MAUI Documentation](https://learn.microsoft.com/en-us/dotnet/maui/)
- [Microsoft Learn - Styles in XAML](https://learn.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/styles/xaml/)
- [Resource Dictionaries and Styles](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/resource-dictionaries?view=net-maui-8.0)

## Overview of Explicit Styles
**Explicit Styles** in **.NET MAUI** are styles that are applied to UI elements only when explicitly referenced. They provide a powerful way to define reusable design elements that you can selectively apply to specific controls by using a `Style` key. Unlike **Implicit Styles**, which automatically apply to all instances of a control type, **Explicit Styles** must be assigned explicitly to individual controls.

Explicit styles are particularly useful when you want to apply a consistent set of properties to a specific set of UI elements without affecting other similar elements in your application.

## Key Features
- **Selective Application**: Applied only to controls that explicitly reference the style using a `Style` key.
- **Reusability**: Can be defined once and reused across multiple UI elements throughout the application, ensuring consistency.
- **Customizable**: Can be customized for individual controls as needed without affecting other instances.

### Explicit Styles vs. Implicit Styles
| Feature                      | Explicit Styles                                  | Implicit Styles                            |
|------------------------------|--------------------------------------------------|--------------------------------------------|
| **Application**              | Must be referenced explicitly using a `Style` key| Automatically applied to elements          |
| **Ease of Use**              | Requires explicit reference                      | Applied without explicit reference         |
| **Targeting Specific Controls** | More precise control over which elements use the style | Applies to all elements of the target type |

## Example of Explicit Styles
Here is an example of how to use explicit styles in a .NET MAUI application to style buttons.

### App.xaml Example
Define an explicit style for `Button` and `Label` controls in `App.xaml`:

```xml
<Application xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.App">
    <Application.Resources>
        <ResourceDictionary>
            <!-- Explicit Style for Button -->
            <Style x:Key="PrimaryButtonStyle" TargetType="Button">
                <Setter Property="BackgroundColor" Value="DarkBlue" />
                <Setter Property="TextColor" Value="White" />
                <Setter Property="FontAttributes" Value="Bold" />
                <Setter Property="CornerRadius" Value="10" />
            </Style>

            <!-- Explicit Style for Label -->
            <Style x:Key="HeaderLabelStyle" TargetType="Label">
                <Setter Property="TextColor" Value="Black" />
                <Setter Property="FontSize" Value="24" />
                <Setter Property="HorizontalOptions" Value="Center" />
            </Style>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```
### Explanation
- **x:Key**: Specifies the unique key for each style (`PrimaryButtonStyle`, `HeaderLabelStyle`). This key is used to explicitly apply the style to specific UI elements.
- **TargetType**: Defines which type of control the style applies to (e.g., `Button`, `Label`).
- **Setters**: Set specific property values for the targeted control.

### Applying Explicit Styles
Once the style is defined, it must be explicitly applied to UI elements using the `Style` attribute and the specified `x:Key`.

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.MainPage">
    <StackLayout Padding="20">
        <Button Text="Click Me" Style="{StaticResource PrimaryButtonStyle}" />
        <Label Text="Welcome to .NET MAUI!" Style="{StaticResource HeaderLabelStyle}" />
    </StackLayout>
</ContentPage>
```
- **Style Attribute**: The `Style` attribute is used to reference the defined explicit style using `{StaticResource <StyleKey>}`.
- **PrimaryButtonStyle**: The button uses the style defined as `PrimaryButtonStyle` to get the specified background color, text color, font attributes, and corner radius.
- **HeaderLabelStyle**: The label applies the style defined as `HeaderLabelStyle`.

## Practical Use Cases
### When to Use Explicit Styles
- **Specific Elements**: When you need a particular set of UI elements to have a distinct appearance compared to others in the application.
- **Reusability for Similar Components**: To define styles that are reused for similar components across multiple pages without applying them globally to all instances of a particular type.
- **Custom Visual Elements**: When you have multiple elements of the same type but want some of them to have different visual properties based on their purpose or functionality.

### Example Scenarios
- **Primary vs. Secondary Buttons**: You might have a `PrimaryButtonStyle` for main actions and a `SecondaryButtonStyle` for secondary actions. Explicit styles allow you to easily differentiate these buttons.
- **Header vs. Regular Labels**: Use explicit styles for headers and regular labels to visually distinguish between different types of text in the UI.
- **Theming Different Sections**: You might use explicit styles to apply different themes to different sections of an app without affecting the entire application.

## Summary Table of Key Elements
| Component                      | Description                                      |
|--------------------------------|--------------------------------------------------|
| **Explicit Style**             | Style applied only when explicitly referenced using a `Style` key. |
| **x:Key**                      | The unique identifier for each style.            |
| **TargetType**                 | Specifies the type of control the style applies to (e.g., `Button`). |
| **Setters**                    | Defines the property values for the styled controls (e.g., `BackgroundColor`, `FontSize`). |
| **StaticResource**             | Used to reference the defined explicit style.    |

## Explicit Styles vs. Implicit Styles Summary Table
| Feature                        | Explicit Styles                                  | Implicit Styles                            |
|--------------------------------|--------------------------------------------------|--------------------------------------------|
| **Application Method**         | Must be referenced explicitly using a `Style` key| Automatically applied to elements of the specified type |
| **Ease of Use**                | Requires explicit reference                      | No need for explicit reference; applies globally to target type |
| **Target Control**             | Specific, allows for more control over which elements use the style | Applies to all elements of the target type |
| **Use Case**                   | When you need to apply styles selectively        | When you want a consistent style across all elements of a type |


## Overview of applying styles to derived types.
In **.NET MAUI**, **styles** are commonly used to achieve a consistent look and feel across UI elements. You can apply styles not only to specific control types (such as `Button` or `Label`), but also to **derived types**—meaning, styles defined for a base type can be applied to any of its derived types. This is particularly useful for ensuring that custom controls based on a base class inherit the intended styles without extra configuration.

## Key Features of Applying Styles to Derived Types
- **Inheritance of Styles**: A style applied to a base control type can be inherited by any derived control, making it easier to maintain a consistent appearance throughout the application.
- **Automatic Application**: Any custom or derived type that is based on a styled type will automatically receive the same style unless explicitly overridden.
- **Reduced Redundancy**: By defining styles for base types, you can eliminate the need for creating separate styles for each derived type.

### Explicit vs. Implicit Style Application for Derived Types
| Feature                      | Explicit Styles for Derived Types               | Implicit Styles for Derived Types                |
|------------------------------|-------------------------------------------------|-------------------------------------------------|
| **Ease of Use**              | Requires specific reference using a key         | Automatically applies to all derived elements    |
| **Application**              | Applied using `x:Key` for specific derived types| Applied to all derived controls without a key    |
| **Use Case**                 | When you need custom styles for derived controls| When you want consistent styles across base and derived controls |

## Example of Applying Styles to Derived Types
Suppose you have a base type `Button`, and you want to apply a style to all buttons, including any custom button types derived from `Button` (e.g., `CustomButton`). You can define a style for `Button` in your `App.xaml`, and that style will automatically be applied to all buttons, including derived types.

### App.xaml Example
Define a global style for `Button` in `App.xaml`:

```xml
<Application xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.App">
    <Application.Resources>
        <ResourceDictionary>
            <!-- Style for Button, which applies to all derived button types -->
            <Style TargetType="Button">
                <Setter Property="BackgroundColor" Value="LightGreen" />
                <Setter Property="TextColor" Value="Black" />
                <Setter Property="FontAttributes" Value="Bold" />
                <Setter Property="CornerRadius" Value="15" />
            </Style>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```
### Explanation
- **TargetType="Button"**: This style applies to all instances of `Button` and its derived types. For example, if you create a custom button class called `CustomButton` that inherits from `Button`, it will automatically receive this style.
- **Setters**: Set properties like `BackgroundColor`, `TextColor`, and `CornerRadius` for all `Button` types, including derived controls.

### Applying to Derived Types
Consider you have a custom class called `CustomButton` that extends `Button`:

```csharp
public class CustomButton : Button
{
    // Custom properties or methods can be defined here
}
```
When you use `CustomButton` in your XAML file, it will automatically inherit the style defined for `Button` without requiring any additional style definitions.

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.MainPage">
    <StackLayout Padding="20">
        <!-- CustomButton inherits the style applied to Button -->
        <local:CustomButton Text="Custom Styled Button" />
    </StackLayout>
</ContentPage>
```
- **CustomButton**: Since `CustomButton` is derived from `Button`, it automatically applies the style defined for `Button` in the `App.xaml`.

## When to Use Styles for Derived Types
- **Custom Control Libraries**: When building custom controls that extend existing controls, applying styles to the base type ensures all derived controls maintain a consistent look without extra configuration.
- **Consistency Across Multiple Control Types**: By applying a style to a base type, you can ensure that all derived versions (including custom variants) have a uniform design.
- **Reduced Complexity**: Simplifies maintenance by eliminating the need to define multiple styles for different derived types that share the same visual properties.

## Summary Table of Key Elements
| Component                      | Description                                      |
|--------------------------------|--------------------------------------------------|
| **Base Type**                  | The original control type to which the style is applied (e.g., `Button`). |
| **Derived Type**               | A custom control type that inherits from the base type (e.g., `CustomButton`). |
| **TargetType**                 | Specifies the type of control the style applies to (e.g., `Button`), which also applies to its derived types. |
| **Automatic Inheritance**      | Derived types automatically receive the style unless overridden explicitly. |

## Overview of Global Styles
**Global Styles** in **.NET MAUI** are styles defined at the application level that can be applied across all pages and controls within an app. They enable developers to ensure a consistent look and feel throughout the entire application by defining reusable style rules in a central location, typically in the `App.xaml` file. This approach allows for efficient maintenance of styling across the app, making it easier to modify the appearance of multiple controls without individually changing each one.

Global styles are particularly powerful for ensuring that common UI elements such as **buttons**, **labels**, and **entries** have a unified design, providing a cohesive user experience.

## Key Features of Global Styles
- **Consistency**: Ensures that the same visual style is applied across the entire application.
- **Centralized Management**: All styles are defined in a central location (`App.xaml`), making it easy to update and manage the appearance of the entire application.
- **Scalable**: Changes made to a global style will automatically propagate to all controls that use the style, which can be highly beneficial for large projects.

### Global vs. Local Styles
| Feature                      | Global Styles                                    | Local Styles                                    |
|------------------------------|--------------------------------------------------|-------------------------------------------------|
| **Scope**                    | Applies throughout the entire application        | Applies only to a specific page or control      |
| **Ease of Maintenance**      | Easier to maintain as styles are in one central place | Harder to maintain, as changes need to be replicated in multiple places |
| **Use Case**                 | Consistent styling across the entire app         | Specific styling for individual elements        |

## Example of Global Styles
To create a **Global Style** in **.NET MAUI**, you define styles in the `App.xaml` file. This style will then be accessible and applied to all relevant controls throughout the application without explicitly referencing them every time.

### App.xaml Example
Define global styles for common controls like `Button` and `Label` in `App.xaml`:

```xml
<Application xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.App">
    <Application.Resources>
        <ResourceDictionary>
            <!-- Global Style for Button -->
            <Style TargetType="Button">
                <Setter Property="BackgroundColor" Value="Blue" />
                <Setter Property="TextColor" Value="White" />
                <Setter Property="FontAttributes" Value="Bold" />
                <Setter Property="Padding" Value="10" />
            </Style>

            <!-- Global Style for Label -->
            <Style TargetType="Label">
                <Setter Property="TextColor" Value="DarkGray" />
                <Setter Property="FontSize" Value="18" />
                <Setter Property="HorizontalOptions" Value="Center" />
            </Style>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```
### Explanation
- **TargetType**: Specifies the type of control the style applies to (e.g., `Button`, `Label`). This means that every button or label in the app will automatically use these styles unless overridden.
- **Setters**: Define specific property values that apply to the targeted control. For example, all buttons will have a blue background, white text, and bold font.

### Applying Global Styles
Once these global styles are defined, they are automatically applied to all `Button` and `Label` controls in the application without any need for explicit reference.

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="YourNamespace.MainPage">
    <StackLayout Padding="20">
        <!-- This button automatically uses the global button style -->
        <Button Text="Click Me" />
        <!-- This label automatically uses the global label style -->
        <Label Text="Welcome to .NET MAUI!" />
    </StackLayout>
</ContentPage>
```
- The `Button` and `Label` elements will inherit the styles defined globally in `App.xaml`.

## Practical Use Cases
### When to Use Global Styles
- **Consistent Look Across App**: When you want all controls of the same type (e.g., all buttons) to look consistent across the application.
- **Centralized Control of Styles**: When you want to manage all styles in one place, allowing changes to propagate easily across the entire app.
- **Large Applications**: Global styles are particularly useful for large applications where it would be inefficient to style each control individually.

## Summary Table of Key Elements
| Component                      | Description                                      |
|--------------------------------|--------------------------------------------------|
| **Global Style**               | A style defined in `App.xaml` that applies to all instances of a specified control type. |
| **TargetType**                 | Specifies the type of control the global style applies to (e.g., `Button`, `Label`). |
| **Setters**                    | Defines the property values for the styled controls (e.g., `BackgroundColor`, `FontSize`). |
| **Centralized Management**     | Allows for easier maintenance and consistency across the application. |



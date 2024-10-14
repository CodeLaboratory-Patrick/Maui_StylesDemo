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

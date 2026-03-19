---
name: implementing-kanban-boards
description: Guide for implementing Syncfusion .NET MAUI Kanban Board (SfKanban) control. Use this skill ALWAYS when user needs kanban boards, task management visualizations, workflow tracking, agile boards, or card-based task management in .NET MAUI applications. Covers installation, data binding with default and custom models, card customization, column configuration, workflow transitions, drag-and-drop events, sorting, localization, and visual styling including liquid glass effects.
metadata:
  author: "Syncfusion Inc"
  version: "3.4.4"
  category: "Data Visualization"
---

# Implementing Kanban Boards in .NET MAUI

## When to Use This Skill

Use this skill when the user needs to:

- **Implement kanban boards** in .NET MAUI applications for task management
- **Visualize workflows** at various stages of completion (To Do, In Progress, Done, etc.)
- **Create agile boards** for sprint planning and task tracking
- **Build card-based interfaces** for organizing and managing items across columns
- **Add drag-and-drop functionality** for moving tasks between workflow stages
- **Implement WIP limits** (Work In Progress) for columns
- **Configure workflow transitions** with restrictions on card movement
- **Customize card templates** with custom data models and visual designs
- **Add task categorization** and status indicators
- **Support RTL/LTR layouts** with localization for international audiences

This skill covers the **Syncfusion .NET MAUI Kanban Board (SfKanban)** control, which provides an efficient way to visualize and manage workflows with rich customization options.

## Component Overview

The **SfKanban** control is a highly interactive and customizable kanban board for .NET MAUI applications. It enables:

- **Workflow visualization** across multiple stages (columns)
- **Drag-and-drop** card movement between columns
- **Work-in-progress (WIP) limits** to control task flow
- **Flexible data binding** with default or custom models
- **Rich card customization** including templates, images, tags, and indicators
- **Column management** with auto-generation or manual configuration
- **Workflow rules** to restrict card transitions
- **Events** for card interactions and state changes
- **Sorting and filtering** capabilities
- **Localization** for multi-language support
- **Visual effects** including liquid glass styling

**Key Features:**
- Visualize the workflow of any process
- Limit work in progress (WIP)
- Manage workflow transitions with allowed/blocked states
- Customize at a high level (cards, columns, themes)
- Smooth transitions within processes
- Support for both default and custom data models

## Documentation and Navigation Guide

### Getting Started

📄 **Read:** [references/getting-started.md](references/getting-started.md)

**When to read:** User needs to set up SfKanban for the first time, install packages, or create their first kanban board.

**Topics covered:**
- Prerequisites (Visual Studio 2022, VS Code, JetBrains Rider)
- Installing Syncfusion.Maui.Kanban NuGet package
- Registering the handler with ConfigureSyncfusionCore
- Basic SfKanban initialization in XAML and C#
- Creating your first kanban board
- Running and testing the application

### Data Binding

📄 **Read:** [references/data-binding.md](references/data-binding.md)

**When to read:** User needs to populate kanban with data, use default KanbanModel, create custom data models, or configure ItemsSource.

**Topics covered:**
- Using default KanbanModel with built-in properties
- Creating custom data models with data mapping
- Setting up ItemsSource with ObservableCollection
- Understanding ColumnMappingPath for column categorization
- AutoGenerateColumns vs manual column definition
- ViewModel pattern for MVVM architecture
- Binding context configuration

### Cards

📄 **Read:** [references/cards.md](references/cards.md)

**When to read:** User needs to customize card appearance, add images, tags, indicators, or create custom card templates.

**Topics covered:**
- Card properties (Title, ImageURL, Category, Description, ID)
- IndicatorFill for status colors
- Tags collection for labels
- CardTemplate for complete customization
- Image handling (assembly reference vs local paths)
- Card layout and design patterns
- Default vs custom card UI
- BindingContext for custom models

### Columns

📄 **Read:** [references/columns.md](references/columns.md)

**When to read:** User needs to configure columns, set width constraints, define categories, enable WIP limits, or customize column appearance.

**Topics covered:**
- Column sizing (MinimumColumnWidth, MaximumColumnWidth, ColumnWidth)
- Categorizing columns with Categories property
- AutoGenerateColumns configuration
- Manual column definition with KanbanColumn
- Multiple categories per column
- Work-in-progress (WIP) limits (MinimumLimit, MaximumLimit)
- Column templates and customization
- Column headers and titles

### Workflows

📄 **Read:** [references/workflows.md](references/workflows.md)

**When to read:** User needs to restrict card movement, define allowed transitions, or prevent drag-and-drop on specific columns.

**Topics covered:**
- KanbanWorkflow class definition
- Category property for source state
- AllowedTransitions for target states
- Restricting card movement between columns
- Preventing specific transitions
- Workflow validation
- State management examples

### Events

📄 **Read:** [references/events.md](references/events.md)

**When to read:** User needs to handle drag-and-drop events, card taps, or respond to card interactions.

**Topics covered:**
- Drag and drop event handling
- DragStart, DragOver, DragEnd events
- Card tapped/clicked events
- Event arguments and data access
- Custom event handlers
- Preventing or allowing drag operations
- Event-based validation

### Sorting

📄 **Read:** [references/sorting.md](references/sorting.md)

**When to read:** User needs to sort cards within columns or implement custom sorting logic.

**Topics covered:**
- Sorting configuration
- Custom sorting logic
- Sort order options (ascending, descending)
- Multiple sort keys
- IComparer implementation

### Advanced Features

📄 **Read:** [references/advanced-features.md](references/advanced-features.md)

**When to read:** User needs RTL support, localization, or multi-language configuration.

**Topics covered:**
- Flow direction (LeftToRight, RightToLeft)
- Localization support for international apps
- Resource file configuration
- Multi-language setup
- Culture-specific formatting

### Customization and Styling

📄 **Read:** [references/customization.md](references/customization.md)

**When to read:** User needs visual customization, liquid glass effect, theme integration, or migration guidance.

**Topics covered:**
- Liquid glass effect for modern UI styling
- Visual customization techniques
- Theme integration with application themes
- Custom templates for cards and columns
- Styling best practices
- Migration guidance from older versions

## Quick Start Example

Here's a minimal example to get started with SfKanban in .NET MAUI:

### Step 1: Install Package

```bash
dotnet add package Syncfusion.Maui.Kanban
```

### Step 2: Register Handler

In `MauiProgram.cs`:

```csharp
using Syncfusion.Maui.Core.Hosting;

public static class MauiProgram
{
    public static MauiApp CreateMauiApp()
    {
        var builder = MauiApp.CreateBuilder();
        builder
            .UseMauiApp<App>()
            .ConfigureSyncfusionCore()  // Register Syncfusion handler
            .ConfigureFonts(fonts =>
            {
                fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
            });

        return builder.Build();
    }
}
```

### Step 3: Create Basic Kanban Board

**XAML:**

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:kanban="clr-namespace:Syncfusion.Maui.Kanban;assembly=Syncfusion.Maui.Kanban"
             x:Class="MyApp.MainPage">
    
    <kanban:SfKanban x:Name="kanban"
                     AutoGenerateColumns="False"
                     ItemsSource="{Binding Cards}">
        <kanban:SfKanban.Columns>
            <kanban:KanbanColumn Title="To Do" Categories="Open" />
            <kanban:KanbanColumn Title="In Progress" Categories="In Progress" />
            <kanban:KanbanColumn Title="Done" Categories="Done" />
        </kanban:SfKanban.Columns>
        <kanban:SfKanban.BindingContext>
            <local:KanbanViewModel />
        </kanban:SfKanban.BindingContext>
    </kanban:SfKanban>
    
</ContentPage>
```

**ViewModel:**

```csharp
using Syncfusion.Maui.Kanban;
using System.Collections.ObjectModel;

public class KanbanViewModel
{
    public ObservableCollection<KanbanModel> Cards { get; set; }
    
    public KanbanViewModel()
    {
        Cards = new ObservableCollection<KanbanModel>
        {
            new KanbanModel
            {
                ID = 1,
                Title = "Review requirements",
                Category = "Open",
                Description = "Analyze customer requirements",
                IndicatorFill = Colors.Red,
                Tags = new List<string> { "High Priority", "Customer" }
            },
            new KanbanModel
            {
                ID = 2,
                Title = "Design prototype",
                Category = "In Progress",
                Description = "Create UI mockups",
                IndicatorFill = Colors.Orange,
                Tags = new List<string> { "Design", "UI" }
            },
            new KanbanModel
            {
                ID = 3,
                Title = "Deploy to production",
                Category = "Done",
                Description = "Release version 1.0",
                IndicatorFill = Colors.Green,
                Tags = new List<string> { "Release" }
            }
        };
    }
}
```

This creates a basic three-column kanban board with sample cards.

## Common Patterns

### Pattern 1: Custom Data Model with Mapping

When you need to use your own data model instead of KanbanModel:

```csharp
// Custom model
public class TaskDetails
{
    public string TaskTitle { get; set; }
    public string TaskDescription { get; set; }
    public string Status { get; set; }
}

// In XAML
<kanban:SfKanban ItemsSource="{Binding Tasks}"
                 ColumnMappingPath="Status">
    <kanban:SfKanban.CardTemplate>
        <DataTemplate>
            <!-- Custom card UI -->
        </DataTemplate>
    </kanban:SfKanban.CardTemplate>
</kanban:SfKanban>
```

**When to use:** You have existing data models and don't want to convert to KanbanModel.

### Pattern 2: Workflow Restrictions

Restrict card movement to enforce workflow rules:

```csharp
kanban.Workflows = new List<KanbanWorkflow>
{
    new KanbanWorkflow
    {
        Category = "Open",
        AllowedTransitions = new List<object> { "In Progress" }
    },
    new KanbanWorkflow
    {
        Category = "In Progress",
        AllowedTransitions = new List<object> { "Code Review", "Open" }
    },
    new KanbanWorkflow
    {
        Category = "Code Review",
        AllowedTransitions = new List<object> { "Done", "In Progress" }
    }
};
```

**When to use:** You need to enforce specific workflow transitions (e.g., can't move from "To Do" directly to "Done").

### Pattern 3: WIP Limits

Control the number of cards in columns:

```xml
<kanban:KanbanColumn Title="In Progress"
                     Categories="In Progress"
                     MinimumLimit="2"
                     MaximumLimit="5" />
```

**When to use:** Implementing agile methodologies where work-in-progress should be limited to maintain focus.

### Pattern 4: Event-Driven Validation

Validate or cancel drag operations:

```csharp
kanban.DragEnd += (sender, e) =>
{
    // Access card data
    var card = e.Data as KanbanModel;
    
    // Validate business rules
    if (card.Category == "Done" && !IsTaskComplete(card))
    {
        e.Cancel = true;
        DisplayAlert("Cannot move to Done", "Task is incomplete", "OK");
    }
};
```

**When to use:** You need custom validation beyond workflow rules (e.g., checking external state).

## Key Properties

### SfKanban Properties

| Property | Type | Description |
|----------|------|-------------|
| `ItemsSource` | IEnumerable | Collection of items to display as cards |
| `ColumnMappingPath` | string | Property name for column categorization |
| `AutoGenerateColumns` | bool | Auto-create columns from data (default: true) |
| `Columns` | ObservableCollection | Manual column definitions |
| `CardTemplate` | DataTemplate | Custom template for card appearance |
| `MinimumColumnWidth` | double | Minimum width for columns |
| `MaximumColumnWidth` | double | Maximum width for columns |
| `ColumnWidth` | double | Fixed width for all columns |
| `Workflows` | List&lt;KanbanWorkflow&gt; | Workflow transition rules |

### KanbanModel Properties (Default)

| Property | Type | Description |
|----------|------|-------------|
| `ID` | object | Unique identifier for the card |
| `Title` | string | Card title text |
| `Description` | string | Card description text |
| `Category` | object | Column category (determines placement) |
| `ImageURL` | string | Image path for card avatar |
| `IndicatorFill` | Color | Status indicator color |
| `Tags` | List&lt;string&gt; | Collection of tags/labels |

### KanbanColumn Properties

| Property | Type | Description |
|----------|------|-------------|
| `Title` | string | Column header title |
| `Categories` | List&lt;object&gt; | Categories mapped to this column |
| `MinimumLimit` | int | Minimum WIP limit |
| `MaximumLimit` | int | Maximum WIP limit |

## Common Use Cases

### 1. Agile Sprint Board

**Scenario:** Team needs a sprint board for tracking user stories.

**Implementation:**
- Columns: Backlog, To Do, In Progress, Testing, Done
- WIP limits on "In Progress" (3-5 items)
- Workflow rules preventing backtracking
- Tags for story points and priority
- Custom card template showing assignee

**See:** [references/data-binding.md](references/data-binding.md), [references/workflows.md](references/workflows.md)

### 2. Personal Task Manager

**Scenario:** Individual user wants to organize personal tasks.

**Implementation:**
- Simple columns: To Do, Doing, Done
- No WIP limits
- Color-coded indicators for priority
- Drag-and-drop enabled
- Minimal workflow restrictions

**See:** [references/getting-started.md](references/getting-started.md), [references/cards.md](references/cards.md)

### 3. Support Ticket System

**Scenario:** Customer support team tracking ticket lifecycle.

**Implementation:**
- Columns: New, Assigned, In Progress, Waiting for Customer, Resolved
- Strict workflow transitions
- Custom data model with ticket properties
- Event handlers for status changes
- Integration with backend API

**See:** [references/data-binding.md](references/data-binding.md), [references/events.md](references/events.md), [references/workflows.md](references/workflows.md)

### 4. Manufacturing Process Board

**Scenario:** Factory floor tracking work orders through stages.

**Implementation:**
- Columns matching production stages
- WIP limits based on capacity
- Custom card templates with QR codes
- RTL support for regional facilities
- Localized for multiple languages

**See:** [references/advanced-features.md](references/advanced-features.md), [references/columns.md](references/columns.md)

### 5. Content Publishing Workflow

**Scenario:** Editorial team managing content from draft to published.

**Implementation:**
- Columns: Ideas, Draft, Review, Editing, Ready, Published
- Workflow restrictions (can't skip review)
- Custom sorting by due date
- Rich card template with author images
- Tags for content type

**See:** [references/workflows.md](references/workflows.md), [references/sorting.md](references/sorting.md), [references/cards.md](references/cards.md)

## Navigation Tips

1. **Start with Getting Started** if setting up for the first time
2. **Read Data Binding** to understand how to populate data
3. **Check Cards and Columns** for visual customization
4. **Add Workflows** when you need transition rules
5. **Implement Events** for custom business logic
6. **Explore Advanced Features** for localization and RTL
7. **Apply Customization** for visual effects and theming

## Related Components

For related data visualization needs in Syncfusion .NET MAUI:
- **Charts** - For graphical data representation
- **DataGrid** - For tabular data display
- **TreeView** - For hierarchical data
- **ListView** - For simple list displays

## Support and Resources

- **GitHub Sample:** [SyncfusionExamples/GettingStarted_Kanban_MAUI](https://github.com/SyncfusionExamples/GettingStarted_Kanban_MAUI)
- **Video Tutorial:** [YouTube - .NET MAUI Kanban Board](https://youtu.be/Mq55vjT7ZEA)
- **API Reference:** [help.syncfusion.com/cr/maui/Syncfusion.Maui.Kanban.SfKanban.html](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Kanban.SfKanban.html)
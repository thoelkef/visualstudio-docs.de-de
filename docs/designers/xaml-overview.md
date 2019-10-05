---
title: Übersicht über XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68823916"
---
# <a name="overview-of-xaml"></a>Übersicht über XAML

Bei Extensible Application Markup Language (XAML) handelt es sich um eine deklarative Sprache, die auf XML basiert. XAML wird häufig in den folgenden Anwendungstypen zum Erstellen von Benutzeroberflächen verwendet:

- [Windows Presentation Foundation-Apps (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Universelle Windows-Plattform-Apps (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)

Der folgende XAML-Code definiert ein einfaches Schaltflächen-Steuerelement.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML wird auch zum Definieren von Workflows in [Windows Workflow Foundation-Apps (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml) verwendet.

## <a name="xaml-designer"></a>XAML-Designer

Visual Studio und Blend für Visual Studio beinhalten einen XAML-Designer, der Sie beim Erstellen von Benutzeroberflächen (UI) für WPF-, UWP-und Xamarin.Forms-Apps unterstützt. Sie können Steuerelemente aus dem Fenster „Toolbox“ oder „Objekte“ ziehen und Eigenschaften im Eigenschaftenfenster festlegen. Wenn Sie diese Aktionen ausführen, erstellen Visual Studio und Blend für Visual Studio den entsprechenden XAML-Code. Wenn Sie den XAML-Code direkt bearbeiten möchten, ist dies ebenfalls möglich.

In den Artikeln in dieser Dokumentationsreihe wird der XAML-Designer in Visual Studio und Blend für Visual Studio erläutert.

## <a name="see-also"></a>Siehe auch

- [XAML in WPF-Apps](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)
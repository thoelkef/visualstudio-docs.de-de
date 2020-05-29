---
title: Übersicht über XAML
ms.date: 05/20/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97f3bc7777023903d5fc38ad1bda7cde45b683b6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183482"
---
# <a name="overview-of-xaml"></a>Übersicht über XAML

Bei Extensible Application Markup Language (XAML) handelt es sich um eine deklarative Sprache, die auf XML basiert. XAML wird häufig in den folgenden Anwendungstypen zum Erstellen von Benutzeroberflächen verwendet:

- [WPF-Apps (Windows Presentation Foundation)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Universelle Windows-Plattform-Apps (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)

Der folgende XAML-Code definiert ein einfaches Schaltflächen-Steuerelement.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML wird auch zum Definieren von Workflows in [Windows Workflow Foundation-Apps (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml) verwendet.

## <a name="xaml-designer"></a>XAML-Designer

Visual Studio und Blend für Visual Studio beinhalten einen XAML-Designer, der Sie beim Erstellen von Benutzeroberflächen (UI) für WPF-, UWP-und Xamarin.Forms-Apps unterstützt. Sie können Steuerelemente aus dem Fenster „Toolbox“ oder „Objekte“ ziehen und Eigenschaften im Eigenschaftenfenster festlegen. Wenn Sie dies tun, erstellen Visual Studio und Blend für Visual Studio den entsprechenden XAML-Code. Wenn Sie den XAML-Code direkt bearbeiten möchten, ist dies ebenfalls möglich.

In den Artikeln in dieser Dokumentationsreihe wird der XAML-Designer in Visual Studio und Blend für Visual Studio erläutert.

## <a name="whats-new"></a>Neuigkeiten

Die neuesten Informationen finden Sie im Blogbeitrag [Neuerungen in den XAML-Entwicklertools in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) , den [Verbesserungen an XAML-Tools in Visual Studio 2019, Version 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/) und den [neuen XAML-Funktionen in Visual Studio](https://youtu.be/yI9OyA4ZM2E) Video auf YouTube.

## <a name="see-also"></a>Siehe auch

- [XAML in WPF-Apps](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)

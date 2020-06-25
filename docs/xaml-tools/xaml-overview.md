---
title: Übersicht über XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331953"
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

## <a name="xaml-code-editor"></a>XAML-Code-Editor

Der [XAML-Code-Editor](xaml-code-editor.md) in der Visual Studio-IDE enthält alle Tools, die Sie zum Erstellen von WPF-und UWP-Apps für die Windows-Plattform und xamarin. Forms benötigen. Obwohl die IDE (integrierte Entwicklungsumgebung) in Visual Studio viele Features bietet, die Sie zum Entwickeln von Apps für andere Plattformen verwenden können, verfügt sie auch über einige Features, die auch für XAML spezifisch sind.

## <a name="xaml-designer"></a>XAML-Designer

Visual Studio und Blend für Visual Studio bieten eine [XAML-Designer](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) , die Sie beim Erstellen von Benutzeroberflächen (UI) für WPF-, UWP-und xamarin. Forms-Apps unterstützt. Sie können Steuerelemente aus dem Fenster „Toolbox“ oder „Objekte“ ziehen und Eigenschaften im Eigenschaftenfenster festlegen. Wenn Sie dies tun, erstellen Visual Studio und Blend für Visual Studio den entsprechenden XAML-Code. Wenn Sie den XAML-Code direkt bearbeiten möchten, ist dies ebenfalls möglich.

## <a name="whats-new"></a>Neues

Die neuesten Informationen finden Sie in den folgenden Ressourcen:

- Die **[Verbesserungen an XAML-Tools in Visual Studio 2019 Version 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** -Blogbeitrag
- Der Blogbeitrag **[zu den Neuerungen in XAML Developer Tools in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- Die **[neuen XAML-Funktionen in Visual Studio](https://youtu.be/yI9OyA4ZM2E)** -Videos auf YouTube

## <a name="see-also"></a>Siehe auch

- [XAML in WPF-Apps](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)

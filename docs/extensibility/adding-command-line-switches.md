---
title: Hinzufügen von Befehls zeilenschaltern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb4abf5352ac6ad78852bd3224df0b22784470db
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903471"
---
# <a name="add-command-line-switches"></a>Befehls Zeilenschalter hinzufügen
Sie können Befehls Zeilenschalter hinzufügen, die für das VSPackage gelten, wenn *devenv.exe* ausgeführt wird. Verwenden <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Sie, um den Namen des Schalters und seine Eigenschaften zu deklarieren. In diesem Beispiel wird der Schalter "mySwitch" für eine Unterklasse von VSPackage mit dem Namen " **addcommandswitchpackage** " ohne Argumente und dem automatischen Laden des VSPackages hinzugefügt.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Die benannten Parameter sind in den folgenden Beschreibungen aufgeführt.

|name|Beschreibung|
|-|-|
| Argumente | Die Anzahl der Argumente für den Schalter. Kann "*" oder eine Liste von Argumenten sein. |
| Einen DemandLoad | Laden Sie das VSPackage automatisch, wenn dies auf 1 festgelegt ist; andernfalls wird 0 festgelegt. |
| HelpString | Die Hilfe Zeichenfolge oder Ressourcen-ID der Zeichenfolge, die mit " **tovenv/?**" angezeigt wird. |
| name | Der-Schalter. |
| PackageGuid | GUID des Pakets |

 Der erste Wert von Argumenten ist in der Regel 0 oder 1. Der spezielle Wert "*" kann verwendet werden, um anzugeben, dass der gesamte Rest der Befehlszeile das Argument ist. Dies kann bei debuggingszenarien nützlich sein, in denen ein Benutzer eine Debugger-Befehls Zeichenfolge übergeben muss.

 Der Wert von DemandLoad ist entweder `true` (1) oder `false` (0) gibt an, dass das VSPackage automatisch geladen werden soll.

 Der HelpString-Wert ist die Ressourcen-ID der Zeichenfolge, die in der Datei "Debug **/?** " angezeigt wird. Anzeige der Hilfe. Dieser Wert sollte in der Form "#NNN" vorliegen, wobei nnn eine ganze Zahl ist. Der Zeichen folgen Wert in der Ressourcen Datei sollte mit einem neuen Zeilenzeichen enden.

 Der Name-Wert ist der Name des Schalters.

 Der packageguid-Wert ist die GUID des Pakets, das diesen Switch implementiert. Die IDE verwendet diese GUID, um das VSPackage in der Registrierung zu finden, für das der Befehls Zeilenschalter gilt.

## <a name="retrieve-command-line-switches"></a>Abrufen von Befehls zeilenschaltern
 Wenn das Paket geladen ist, können Sie die Befehls Zeilenschalter abrufen, indem Sie die folgenden Schritte ausführen.

1. In der VSPackage- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung wird `QueryService` aufgerufen, <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> um die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> Schnittstelle abzurufen.

2. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> Sie auf, um die vom Benutzer eingegebenen Befehls Zeilenschalter abzurufen.

   Der folgende Code zeigt, wie Sie herausfinden, ob der Befehls Zeilenschalter "mySwitch" vom Benutzer eingegeben wurde:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Es liegt in ihrer Verantwortung, die Befehls Zeilenschalter bei jedem Laden des Pakets zu überprüfen.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv-Befehlszeilenparameter](../ide/reference/devenv-command-line-switches.md)
- [Das Dienstprogramm "| atepkgdef"](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef-Dateien](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)

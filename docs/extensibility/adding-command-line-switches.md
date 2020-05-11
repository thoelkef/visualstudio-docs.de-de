---
title: Hinzufügen von Befehlszeilenschaltern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740166"
---
# <a name="add-command-line-switches"></a>Hinzufügen von Befehlszeilenschaltern
Sie können Befehlszeilenschalter hinzufügen, die auf Ihr VSPackage angewendet werden, wenn *devenv.exe* ausgeführt wird. Verwenden <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Sie diese Option, um den Namen des Switches und seine Eigenschaften zu deklarieren. In diesem Beispiel wird der MySwitch-Schalter für eine Unterklasse von VSPackage mit dem Namen **AddCommandSwitchPackage** ohne Argumente und mit dem automatisch geladenen VSPackage hinzugefügt.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Die benannten Parameter werden in den folgenden Beschreibungen angezeigt.

||||
|-|-|-|-|
| Parameter | BESCHREIBUNG|
| Argumente | Die Anzahl der Argumente für den Switch. Kann "*" oder eine Liste von Argumenten sein. |
| DemandLoad | Laden Sie das VSPackage automatisch, wenn dieser auf 1 und andernfalls auf 0 gesetzt ist. |
| Helpstring | Die Hilfezeichenfolge oder Ressourcen-ID der Zeichenfolge, die mit **devenv /?** angezeigt werden soll. |
| name | Der Schalter. |
| PackageGuid | GUID des Pakets |

 Der erste Wert von Arguments ist in der Regel 0 oder 1. Ein spezieller Wert von '*' kann verwendet werden, um anzugeben, dass der gesamte Rest der Befehlszeile das Argument ist. Dies kann nützlich sein für das Debuggen von Szenarien, in denen ein Benutzer eine Debuggerbefehlszeichenfolge übergeben muss.

 Der DemandLoad-Wert `true` ist entweder `false` (1) oder (0) gibt an, dass das VSPackage automatisch geladen werden soll.

 Der HelpString-Wert ist die Ressourcen-ID der Zeichenfolge, die im **devenv /?** angezeigt wird. Hilfeanzeige. Dieser Wert sollte in der Form "#nnn" sein, wobei nnn eine ganze Zahl ist. Der Zeichenfolgenwert in der Ressourcendatei sollte in einem neuen Zeilenzeichen enden.

 Der Name-Wert ist der Name des Switches.

 Der PackageGuid-Wert ist die GUID des Pakets, das diesen Switch implementiert. Die IDE verwendet diese GUID, um das VSPackage in der Registrierung zu finden, auf die der Befehlszeilenschalter angewendet wird.

## <a name="retrieve-command-line-switches"></a>Abrufen von Befehlszeilenschaltern
 Wenn Ihr Paket geladen wird, können Sie die Befehlszeilenschalter abrufen, indem Sie die folgenden Schritte ausführen.

1. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> `QueryService` Sie in der Implementierung Ihres VSPackage die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> Schnittstelle auf. <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>

2. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> Sie den Aufruf zum Abrufen der vom Benutzer eingegebenen Befehlszeilenschalter auf.

   Der folgende Code zeigt, wie Sie herausfinden, ob der Befehlszeilenschalter MySwitch vom Benutzer eingegeben wurde:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Es liegt in Ihrer Verantwortung, bei jedem Laden Ihres Pakets nach Ihren Befehlszeilenwechseln zu suchen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv-Befehlszeilenparameter](../ide/reference/devenv-command-line-switches.md)
- [Dienstprogramm CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef-Dateien](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)

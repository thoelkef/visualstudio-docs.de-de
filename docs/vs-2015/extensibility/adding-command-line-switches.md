---
title: Hinzufügen von Befehls zeilenschaltern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562275"
---
# <a name="adding-command-line-switches"></a>Hinzufügen von Befehlszeilenschaltern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Befehls Zeilenschalter hinzufügen, die für das VSPackage gelten, wenn devenv.exe ausgeführt wird. Verwenden <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Sie, um den Namen des Schalters und seine Eigenschaften zu deklarieren. In diesem Beispiel wird der Schalter "mySwitch" für eine Unterklasse von VSPackage mit dem Namen " **addcommandswitchpackage** " ohne Argumente und dem automatischen Laden des VSPackages hinzugefügt.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Die benannten Parameter sind in der folgenden Tabelle aufgeführt.  
  
 Argumente  
 Die Anzahl der Argumente für den Schalter. Kann "*" oder eine Liste von Argumenten sein.  
  
 Einen DemandLoad  
 Laden Sie das VSPackage automatisch, wenn dies auf 1 festgelegt ist; andernfalls wird 0 festgelegt.  
  
 HelpString  
 Die Hilfe Zeichenfolge oder Ressourcen-ID der Zeichenfolge, die mit " **tovenv/?**" angezeigt wird.  
  
 Name  
 Der-Schalter.  
  
 PackageGuid  
 GUID des Pakets  
  
 Der erste Wert von Argumenten ist in der Regel 0 oder 1. Der spezielle Wert "*" kann verwendet werden, um anzugeben, dass der gesamte Rest der Befehlszeile das Argument ist. Dies kann bei debuggingszenarien nützlich sein, in denen ein Benutzer eine Debugger-Befehls Zeichenfolge übergeben muss.  
  
 Der Wert von DemandLoad ist entweder `true` (1) oder `false` (0) gibt an, dass das VSPackage automatisch geladen werden soll.  
  
 Der HelpString-Wert ist die Ressourcen-ID der Zeichenfolge, die in der Datei "Debug/?" angezeigt wird. Anzeige der Hilfe. Dieser Wert sollte in der Form "#NNN" vorliegen, wobei nnn eine ganze Zahl ist. Der Zeichen folgen Wert in der Ressourcen Datei sollte mit einem neuen Zeilenzeichen enden.  
  
 Der Name-Wert ist der Name des Schalters.  
  
 Der packageguid-Wert ist die GUID des Pakets, das diesen Switch implementiert. Die IDE verwendet diese GUID, um das VSPackage in der Registrierung zu finden, für das der Befehls Zeilenschalter gilt.  
  
## <a name="retrieving-command-line-switches"></a>Abrufen von Befehls zeilenschaltern  
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
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Debug-Befehls Zeilenschalter](../ide/reference/devenv-command-line-switches.md)   
 [Das Dienstprogramm "| atepkgdef"](../extensibility/internals/createpkgdef-utility.md)   
 [PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

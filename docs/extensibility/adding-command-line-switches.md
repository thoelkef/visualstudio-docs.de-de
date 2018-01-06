---
title: "Hinzufügen von Befehlszeilenoptionen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d686e7b68e790c419679bf495bf08ad4cd4807e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-command-line-switches"></a>Hinzufügen von Befehlszeilenoptionen
Sie können Befehlszeilenoptionen hinzufügen, die für Ihr VSPackage gelten, wenn devenv.exe ausgeführt wird. Verwendung <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> der Name des Schalters sowie die Eigenschaften deklariert. In diesem Beispiel wird der MySwitch Schalter für eine Unterklasse von VSPackage mit dem Namen hinzugefügt **AddCommandSwitchPackage** ohne Argumente und mit dem VSPackage automatisch geladen.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Benannte Parameter werden in der folgenden Tabelle gezeigt.  
  
 Argumente  
 Die Anzahl der Argumente für den Switch. Kann "*", oder eine Liste von Argumenten.  
  
 DemandLoad  
 Laden Sie das VSPackage automatisch bei 1, andernfalls auf 0 festgelegt ist.  
  
 HelpString  
 Die Zeichenfolge oder Ressourcen-ID der Zeichenfolge mit anzuzeigende **Devenv /?**.  
  
 name  
 Der Schalter.  
  
 PackageGuid  
 Die GUID des Pakets.  
  
 Der erste Wert von Argumenten ist in der Regel 0 oder 1. Spezielle Wert "*" verwendet werden können, um anzugeben, dass der gesamte Rest der Befehlszeile das Argument ist. Dies kann zum Debuggen von Szenarien, in denen ein Benutzer in einer Befehlszeichenfolge Debugger übergeben muss, hilfreich sein.  
  
 Ist der Wert DemandLoad `true` (1) oder `false` (0) gibt an, dass das VSPackage automatisch geladen werden soll.  
  
 Der HelpString-Wert ist die Ressourcen-ID der Zeichenfolge, die in den Devenv /? Anzeige von Hilfe. Dieser Wert sollte im Format "#nnn" wobei "nnn" eine ganze Zahl ist. Der Zeichenfolgenwert in der Ressourcendatei sollte ein neue-Zeile-Zeichen beendet werden.  
  
 Die Name-Wert ist der Name des Schalters.  
  
 Der PackageGuid-Wert ist die GUID des Pakets, das diesen Schalter implementiert. Die IDE verwendet diese GUID das VSPackage in der Registrierung gefunden, für die die Befehlszeilenoption gilt.  
  
## <a name="retrieving-command-line-switches"></a>Abrufen von Befehlszeilenoptionen  
 Wenn das Paket geladen wird, können Sie die Befehlszeilenschaltern abrufen, durch die folgenden Schritte auszuführen.  
  
1.  In Ihrem VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> -Implementierung, rufen `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> zum Abrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> Schnittstelle.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> die Befehlszeilenschaltern abgerufen, die der Benutzer eingegeben.  
  
 Der folgende Code zeigt, wie Sie herausfinden, ob die Befehlszeilenoption MySwitch vom Benutzer eingegeben wurde:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es liegt in Ihrer Verantwortung jedes Mal, wenn das Paket geladen wird, für die Befehlszeilenoptionen zu überprüfen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef-Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md)   
 [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
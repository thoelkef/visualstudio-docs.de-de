---
title: Hinzufügen von Befehlszeilenschaltern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a67e25b06f9b33f184280d0182cf96bfcda154db
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188749"
---
# <a name="adding-command-line-switches"></a>Hinzufügen von Befehlszeilenschaltern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Befehlszeilenoptionen hinzufügen, die für das VSPackage angewendet werden soll, wenn devenv.exe ausgeführt wird. Verwendung <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> der Name des Schalters sowie die zugehörigen Eigenschaften deklariert. In diesem Beispiel wird der Schalter MySwitch für eine Unterklasse von VSPackage mit dem Namen hinzugefügt **AddCommandSwitchPackage** ohne Argumente und das VSPackage, die automatisch geladen.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 In der folgenden Tabelle werden die benannten Parameter angezeigt.  
  
 Argumente  
 Die Anzahl der Argumente für den Switch. Kann "*", oder eine Liste von Argumenten.  
  
 DemandLoad  
 Laden Sie das VSPackage automatisch, wenn dieser auf 1 fest, legen Sie andernfalls auf 0 festgelegt wird.  
  
 HelpString  
 Die Zeichenfolge "oder" Ressource-ID der Zeichenfolge mit anzuzeigende **Devenv /?**.  
  
 name  
 Der Schalter.  
  
 PackageGuid  
 Die GUID des Pakets.  
  
 Der erste Wert der Argumente ist in der Regel 0 oder 1. Ein spezieller Wert von ' *' kann verwendet werden, um anzugeben, dass der gesamte Rest der Befehlszeile das Argument ist. Dies kann nützlich für Debugszenarien, in dem Benutzer in einer Befehlszeichenfolge Debugger übergeben, muss, sein.  
  
 Der DemandLoad-Wert lautet entweder `true` (1) oder `false` (0) gibt an, dass das VSPackage automatisch geladen werden sollen.  
  
 Der HelpString-Wert ist die Ressourcen-ID der Zeichenfolge, die in den Devenv angezeigt /? Anzeige von Hilfe. Dieser Wert sollte in der Form "#nnn" wobei "nnn" eine ganze Zahl ist. Der Zeichenfolgenwert in der Ressourcendatei sollte auf ein neue-Zeile-Zeichen enden.  
  
 Der Name-Wert ist der Name des Schalters.  
  
 Der Wert des PackageGuid ist die GUID des Pakets, das diesen Schalter implementiert. Die IDE verwendet diese GUID, die das VSPackage in der Registrierung gefunden, für die die Befehlszeilenoption gilt.  
  
## <a name="retrieving-command-line-switches"></a>Abrufen von Befehlszeilenschaltern  
 Wenn das Paket geladen wird, können Sie die Befehlszeilenschalter abrufen, die folgenden Schritte aus.  
  
1.  In Ihrem VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> -Implementierung, rufen `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> zum Abrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> Schnittstelle.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> die Befehlszeilenschalter abgerufen, die vom Benutzer eingegebene.  
  
 Der folgende Code zeigt, wie Sie herausfinden, ob die Befehlszeilenoption MySwitch vom Benutzer eingegeben wurde:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es ist Ihre Aufgabe, die für Ihre Befehlszeilenschalter überprüfen jedes Mal, wenn das Paket geladen wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef-Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md)   
 [PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)


---
title: "Hinzuf&#252;gen von Befehlszeilenoptionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlszeilenoptionen hinzufügen"
  - "Abrufen von-Befehlszeilenoptionen"
  - "IVsAppCommandLine::GetOption-Methode"
  - "Switches-Befehlszeile"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Hinzuf&#252;gen von Befehlszeilenoptionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Befehlszeilenoptionen hinzufügen, die für das VSPackage gelten, wenn devenv.exe ausgeführt wird. Verwendung <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> der Name des Switches und deren Eigenschaften deklariert. In diesem Beispiel wird der Switch MySwitch für eine Unterklasse von VSPackage mit dem Namen hinzugefügt **AddCommandSwitchPackage** ohne Argumente und mit der VSPackage automatisch geladen.  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Die benannte Parameter werden in der folgenden Tabelle veranschaulicht.  
  
 Argumente  
 Die Anzahl der Argumente für den Switch. Kann "\*", oder eine Liste von Argumenten.  
  
 DemandLoad  
 Laden Sie das VSPackage automatisch, wenn 1, setzen Sie andernfalls auf 0 eingestellt ist.  
  
 HelpString  
 Die Zeichenfolge oder Ressourcen\-ID der Zeichenfolge mit anzuzeigende **Devenv \/?**.  
  
 Name  
 Der Schalter.  
  
 PackageGuid  
 Die GUID des Pakets.  
  
 Der erste Wert der Argumente ist in der Regel 0 oder 1. Ein spezieller Wert von ' \*' kann verwendet werden, um anzugeben, dass der ganze Rest der Befehlszeile das Argument ist. Dies kann nützlich für das Debuggen von Szenarios, in denen ein Benutzer eine Befehlszeichenfolge Debugger übergeben muss, sein.  
  
 Ist der Wert DemandLoad `true` \(1\) oder `false` \(0\) gibt an, dass das VSPackage automatisch geladen werden sollen.  
  
 Der HelpString\-Wert ist die Ressourcen\-ID der Zeichenfolge in den Devenv \/? Hilfe anzeigen. Dieser Wert sollte in der Form "\#nnn" wobei Nnn eine ganze Zahl ist. Der Zeichenfolgenwert in der Ressourcendatei sollte eine neue\-Zeile\-Zeichen beendet.  
  
 Die Name\-Wert ist der Name des Schalters.  
  
 Der Wert von PackageGuid ist die GUID des Pakets, das diesen Schalter implementiert. Die IDE verwendet diese GUID des VSPackage in der Registrierung gefunden, für die die Befehlszeilenoption gilt.  
  
## Abrufen von Befehlszeilenoptionen  
 Wenn das Paket geladen wird, können Sie die Befehlszeilenoptionen abrufen, mithilfe des folgenden Verfahrens.  
  
1.  In Ihrem VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung, rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> zum Abrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> Schnittstelle.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> Befehlszeilenoptionen abrufen, die der Benutzer eingegeben hat.  
  
 Der folgende Code zeigt, wie Sie herausfinden, ob die Befehlszeilenoption MySwitch vom Benutzer eingegeben wurde:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es ist Ihre Aufgabe jedes Mal, wenn das Paket geladen wird, für die Befehlszeilenoptionen zu überprüfen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv\-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef\-Dienstprogramm](../extensibility/internals/createpkgdef-utility.md)   
 [. PKGDEF\-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
---
title: "Elemente der isolierte Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell, isolierten Modus"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemente der isolierte Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Einstellungen in der Registrierung fest und Einstiegspunkt für die Anwendung von Ihrer Anwendung für isolierte Shells, und seine VSCT, PKGDEF, and.pkgundef Dateien ändern.  
  
## Registrierungseinträge  
 Die PKGDEF und die Dateien .pkgundef ändern die Registrierungseinträge für die isolierte Shell\-Anwendung. Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
 Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
1.  Der Registrierungsschlüssel für die Anwendung wird erstellt.  
  
2.  Die Registrierung wird von der PKGDEF\-Datei der Anwendung durch die Definition der angegebenen Schlüssel und die Einträge aktualisiert.  
  
3.  Für jedes Paket, das Teil der Anwendung ist, wird die Registrierung von der PKGDEF\-Datei des Pakets aktualisiert. Jedes Paket ist in der PKGDEF\-Datei der Anwendung definiert, durch die \\Packages\\ $RootKey$ {*VsPackageGuid*} Schlüssel für das Paket.  
  
4.  Die Registrierung wird aktualisiert, aus dem AppEnvConfig.pkgdef und BaseConfig.pkgdef in der *Visual Studio SDK\-Installationspfad*\\Common7\\IDE\\ShellExtensions\\Platform\-Verzeichnis. Diese Dateien sind Teil von Visual Studio und auch Teil des verteilbaren Pakets für Visual Studio\-Shell \(isolierter Modus\).  
  
5.  Die Registrierung wird aus der .pkgundef\-Datei der Anwendung durch Entfernen der angegebenen Schlüssel und die Einträge aktualisiert.  
  
## Laufzeit\-Einstellungen  
 Wenn ein Benutzer die isolierte Shell\-Anwendung startet, ruft er den Eintrag Ausgangspunkt der Visual Studio\-Shell. Anwendungseinstellungen werden definiert, wenn die Anwendung gestartet, wie folgt wird:  
  
1.  Die Visual Studio\-Shell überprüft die anwendungsregistrierung bestimmte Schlüssel. Wenn die Einstellung für einen Schlüssel im Aufruf für den Start\-Einstiegspunkt angegeben wird, überschreibt dieser Wert den Wert in der Registrierung.  
  
2.  Wenn weder für die Registrierung als auch für den Eintrag zeigen Parameter gibt den Wert einer Einstellung, wird der Standardwert für die Einstellung verwendet.  
  
 Wenn ein Benutzer die Anwendung von der Befehlszeile aus gestartet wird, werden alle Befehlszeilenoptionen für die Visual Studio\-Shell übergeben, die sie auf die gleiche Weise behandelt, die Devenv. Weitere Informationen über die Devenv\-Schalter finden Sie unter [Devenv\-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md) und [Devenv\-Befehlszeilenschalter für VSPackage\-Entwicklung](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Weitere Informationen zu Befehlszeilenoptionen wie ein Paket registriert, finden Sie unter [Hinzufügen von Befehlszeilenoptionen](../extensibility/adding-command-line-switches.md).  
  
## Der Einstiegspunkt für den Start  
 Die Appenvstub.dll\-Datei enthält die Einstiegspunkte für den Zugriff auf die isolierte Shell. Beim Starten der Anwendung wird der Start Eintrag Punkt des Appenvstub.dll aufgerufen.  
  
 Sie können das Verhalten der Anwendung ändern, ändern Sie den Wert des letzten Parameters, der für den Start\-Einstiegspunkt übergeben wird. Weitere Informationen finden Sie unter [Isolierte Shell Einstiegspunkt\-Parameter \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## Die. VSCT\-Datei  
 Die VSCT\-Datei können Sie angeben, welche standard\-Visual Studio\-GUI\-Elemente in der Anwendung verfügbar sind. Weitere Informationen finden Sie unter [. VSCT\-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## Die. Pkgundef\-Datei  
 Wenn die Anwendung auf einem Computer installiert ist, auf dem Visual Studio bereits installiert ist, wird eine Kopie der Visual Studio\-Registrierungseinträge für die Anwendung erstellt. Standardmäßig verwendet die Anwendung VSPackages, die bereits auf dem Computer installiert sind. Die .pkgundef\-Datei können Sie Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio\-Shell\-Erweiterungen aus der Anwendung entfernen. Weitere Informationen finden Sie unter [. Pkgundef\-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Die .pkgundef\-Datei können Sie Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio\-Shell\-Erweiterungen aus der Anwendung entfernen. Weitere Informationen finden Sie unter [. Pkgundef\-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Der Satz von Paket\-GUIDs, die Sie ausschließen können in aufgelisteten [Paket\-GUIDs der Visual Studio\-Funktionen](../extensibility/package-guids-of-visual-studio-features.md).  
  
## Die. PKGDEF\-Datei  
 Die PKGDEF\-Datei können Sie die Registrierungseinträge für die Anwendung definieren, die festgelegt werden, wenn die Anwendung installiert ist. Eine Beschreibung der PKGDEF\-Datei und eine Liste der Registrierungseinträge, in denen der Visual Studio\-Shell verwendet werden, finden Sie unter [. PKGDEF\-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## Ersetzen von Zeichenfolgen  
 Verwendet in der PKGDEF und .pkgundef Ersatzzeichenfolgen in aufgelisteten [Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef\-Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## Andere Einstellungen  
 Wenn Ihre Anwendung für isolierte Shells Microsoft.VisualStudio.GraphModel.dll abhängt, müssen Sie die folgende bindungsumleitung .config\-Datei für die isolierte Shell\-Anwendung hinzufügen:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
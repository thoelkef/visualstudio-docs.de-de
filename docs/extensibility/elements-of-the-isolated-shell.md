---
redirect_url: shell/elements-of-the-isolated-shell
title: Elemente der isolierte Shell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b1e52963253f73c633b9b14bf64525bdb0afaeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-the-isolated-shell"></a>Elemente der isolierte Shell
Sie können die registrierungseinstellungen, Einstellungen zur Laufzeit und Einstiegspunkt der Anwendung die isolierte Shell-Anwendung, und seine VSCT PKGDEF, and.pkgundef Dateien ändern.  
  
## <a name="registry-settings"></a>Registrierungseinstellungen  
 Die PKGDEF und die Dateien .pkgundef ändern die registrierungseinstellungen für die isolierte Shell-Anwendung. Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
 Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
1.  Der Registrierungsschlüssel für die Anwendung wird erstellt.  
  
2.  Die Registrierung wird von der PKGDEF-Datei der Anwendung durch die Definition der angegebenen Schlüssel und Einträge aktualisiert.  
  
3.  Für jedes Paket, das Teil der Anwendung ist, wird die Registrierung von der PKGDEF-Datei des Pakets aktualisiert. Jedes Paket ist in der PKGDEF-Datei der Anwendung definiert, durch die $RootKey$ \Packages\\{*VsPackageGuid*} Schlüssel für das Paket.  
  
4.  Die Registrierung wird aktualisiert, aus dem AppEnvConfig.pkgdef und BaseConfig.pkgdef in der *Visual Studio SDK-Installationspfad*\Common7\IDE\ShellExtensions\Platform-Verzeichnis. Diese Dateien sind Teil von Visual Studio und auch das verteilbare Paket für Visual Studio Shell (isolierter Modus).  
  
5.  Die Registrierung wird aus der .pkgundef-Datei der Anwendung durch das Entfernen der angegebenen Schlüssel und Einträge aktualisiert.  
  
## <a name="run-time-settings"></a>Run-Time-Einstellungen  
 Wenn ein Benutzer die isolierten Shell-Anwendung startet, ruft er den Ausgangspunkt der Eintrag der Visual Studio-Shell. Anwendungseinstellungen werden definiert, wenn die Anwendung gestartet, wie folgt wird:  
  
1.  Die Visual Studio-Shell überprüft die anwendungsregistrierung bestimmte Schlüssel. Wenn die Einstellung für einen Schlüssel im Aufruf den Startpunkt für den Eintrag angegeben wird, überschreibt dieser Wert den Wert in der Registrierung.  
  
2.  Wenn weder für die Registrierung als auch für den Eintrag zeigen Parameter gibt den Wert einer Einstellung, wird der Standardwert für die Einstellung verwendet.  
  
 Wenn ein Benutzer die Anwendung über die Befehlszeile gestartet wird, werden alle Befehlszeilenoptionen für die Visual Studio-Shell übergeben, die sie auf die gleiche Weise behandelt, das die Devenv durchführt. Weitere Informationen zu Devenv-Schalter, finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md) und [Devenv-Befehlszeilenschalter für VSPackage-Entwicklung](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Weitere Informationen dazu, wie ein Paket für Befehlszeilenschalter registriert, finden Sie unter [Befehlszeilenoptionen hinzufügen](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Der Einstiegspunkt für den Start  
 Die Appenvstub.dll-Datei enthält die Einstiegspunkte für den Zugriff auf die isolierte Shell. Wenn die Anwendung gestartet wird, wird der Start Eintrag Punkt der Appenvstub.dll aufgerufen.  
  
 Sie können das Verhalten der Anwendung ändern, durch Ändern des Werts des letzten Parameters, der für den Start-Einstiegspunkt übergeben wird. Weitere Informationen finden Sie unter [isolierte Shell Eintrag Punkt Parameter (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Die. VSCT-Datei  
 Die VSCT-Datei können Sie angeben, welche Visual Studio-Benutzeroberfläche Standardelemente in der Anwendung verfügbar sind. Weitere Informationen finden Sie unter [. VSCT-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Die. Pkgundef-Datei  
 Wenn die Anwendung auf einem Computer installiert ist, auf dem Visual Studio bereits installiert ist, erfolgt eine Kopie der Visual Studio-Registrierungseinträge für die Anwendung. Standardmäßig verwendet die Anwendung VSPackages, die bereits auf dem Computer installiert sind. Die Datei .pkgundef können Sie die Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen aus der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Die Datei .pkgundef können Sie die Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen aus der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Der Satz von Paket-GUIDs, die Sie ausschließen können, sind in aufgeführt [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Die. PKGDEF-Datei  
 Die PKGDEF-Datei können Sie die Registrierungseinträge für die Anwendung zu definieren, die festgelegt werden, wenn die Anwendung installiert wird. Eine Beschreibung der PKGDEF-Datei und eine Liste von Registrierungseinträgen, die der Visual Studio-Shell verwendet werden, finden Sie unter [. PKGDEF Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ersetzen von Zeichenfolgen  
 Verwendet in der PKGDEF und .pkgundef Ersatzzeichenfolgen in aufgelisteten [Ersetzung in Zeichenfolgen verwendet. PKGDEF und. Pkgundef Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Weitere Einstellungen  
 Wenn Ihre Anwendung isolierte Shell Microsoft.VisualStudio.GraphModel.dll abhängig ist, müssen Sie die folgende bindungsumleitung in Ihrer Anwendung Isolated Shell-config-Datei hinzufügen:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
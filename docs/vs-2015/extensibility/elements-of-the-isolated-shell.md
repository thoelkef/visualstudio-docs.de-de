---
title: Elemente der Isolated Shell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cea41ee70001d32bb003a6ccefe033d42274f682
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960306"
---
# <a name="elements-of-the-isolated-shell"></a>Elemente der Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die registrierungseinstellungen, Laufzeiteinstellungen und Einstiegspunkt der Anwendung von Ihrem isolated Shell-Anwendung, und die VSCT, PKGDEF, and.pkgundef Dateien ändern.  
  
## <a name="registry-settings"></a>Registrierungseinstellungen  
 Sowohl die pkgundef-Dateien als auch die PKGDEF ändern die registrierungseinstellungen für die isolated Shell-Anwendung. Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
 Wenn die Anwendung ausgeführt wird, werden die Registrierungseinträge in der folgenden Reihenfolge definiert:  
  
1.  Der Schlüssel für die Anwendung wird erstellt.  
  
2.  Die Registrierung wird von der PKGDEF-Datei der Anwendung durch die Definition der angegebenen Schlüssel und -Einträge aktualisiert.  
  
3.  Für jedes Paket, das Teil Ihrer Anwendung ist, wird die Registrierung aus der PKGDEF-Datei des Pakets aktualisiert. Jedes Paket ist in der PKGDEF-Datei der Anwendung definiert, durch die $RootKey$ \Packages\\{*VsPackageGuid*} Schlüssel für das Paket.  
  
4.  Die Registrierung wird aktualisiert, aus dem AppEnvConfig.pkgdef und BaseConfig.pkgdef in die *Visual Studio SDK-Installationspfad*\Common7\IDE\ShellExtensions\Platform-Verzeichnis. Diese Dateien sind Teil von Visual Studio und ihrerseits das verteilbare Paket für Visual Studio Shell (isolierter Modus).  
  
5.  Die Registrierung ist aus der pkgundef-Datei der Anwendung durch das Entfernen der angegebenen Schlüssel und der Einträge aktualisiert.  
  
## <a name="run-time-settings"></a>Laufzeiteinstellungen  
 Wenn ein Benutzer die isolated Shell-Anwendung startet, ruft er den Einstiegspunkt der Start von Visual Studio-Shell. Anwendungseinstellungen werden definiert, wenn die Anwendung gestartet, wie folgt wird:  
  
1. Die Visual Studio-Shell überprüft die anwendungsregistrierung bestimmte Schlüssel. Wenn die Einstellung für einen Schlüssel im Aufruf an den Ausgangspunkt für den Eintrag angegeben ist, überschreibt dieser Wert den Wert in der Registrierung.  
  
2. Wenn weder für die Registrierung als auch für den Eintrag zeigen Parameter gibt den Wert einer Einstellung, wird der Standardwert für die Einstellung verwendet.  
  
   Wenn ein Benutzer Ihrer Anwendung über die Befehlszeile gestartet wird, werden alle Befehlszeilenoptionen an der Visual Studio-Shell, übergeben sie auf die gleiche Weise behandelt, die Devenv ausführt. Weitere Informationen zu den Devenv-Schalter, finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md) und [Devenv-Befehlszeilenschalter für die Entwicklung von VSPackages](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Weitere Informationen dazu, wie ein Paket für Befehlszeilen-Switches registriert wird, finden Sie unter [Befehlszeilenoptionen hinzufügen](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Der Einstiegspunkt für den Start  
 Die Appenvstub.dll-Datei enthält die Einstiegspunkte für den Zugriff auf die isolated Shell. Wenn die Anwendung gestartet wird, ruft er den Start Eintrag Punkt der Appenvstub.dll.  
  
 Sie können das Verhalten der Anwendung ändern, durch Ändern des Werts des letzten Parameters, der für den Start-Einstiegspunkt übergeben wird. Weitere Informationen finden Sie unter [isolierten Shell Eintrag Punkt Parameter (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Die. VSCT-Datei  
 Die VSCT-Datei können Sie angeben, welche Elemente der standardmäßigen Visual Studio-Benutzeroberfläche in der Anwendung verfügbar sind. Weitere Informationen finden Sie unter [. VSCT-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Die. Pkgundef-Datei  
 Wenn die Anwendung auf einem Computer installiert ist, auf dem Visual Studio bereits installiert ist, wird eine Kopie der Visual Studio Registrierungseinträge für die Anwendung erstellt. Standardmäßig verwendet die Anwendung VSPackages, die bereits auf dem Computer installiert sind. Die pkgundef-Datei können Sie die Einträge in der Registrierung ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen von der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Die pkgundef-Datei können Sie die Einträge in der Registrierung ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen von der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Der Satz von Paket-GUIDs, die Sie ausschließen können finden Sie in [-Paket-GUIDs von Visual Studio-Features](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>The .Pkgdef File  
 Die PKGDEF-Datei können Sie die Registrierungseinträge für die Anwendung zu definieren, die festgelegt werden, wenn die Anwendung installiert ist. Eine Beschreibung der PKGDEF-Datei und eine Liste der Registrierungseinträge, die der Visual Studio-Shell verwendet werden, finden Sie unter [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ersetzen von Zeichenfolgen  
 Die Ersatzzeichenfolgen in den PKGDEF- und pkgundef-Dateien verwendet, finden Sie in [Ersetzung in Zeichenfolgen verwendet. PKGDEF und. Pkgundef-Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Weitere Einstellungen  
 Wenn Microsoft.VisualStudio.GraphModel.dll Ihre isolated Shell-Anwendung abhängt, müssen Sie die folgende bindungsumleitung in Ihrer Anwendung Isolated Shell-config-Datei hinzufügen:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

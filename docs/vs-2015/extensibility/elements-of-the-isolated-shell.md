---
title: Elemente der isolierten Shell | Microsoft-Dokumentation
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
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204603"
---
# <a name="elements-of-the-isolated-shell"></a>Elemente der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Registrierungs Einstellungen, die Lauf Zeit Einstellungen und den Anwendungs Einstiegspunkt ihrer isolierten Shellanwendung sowie die vsct-, pkgdef-und pkgundef-Dateien ändern.  
  
## <a name="registry-settings"></a>Registrierungseinstellungen  
 Sowohl die pkgdef-als auch die pkgundef-Dateien ändern die Registrierungs Einstellungen für die isolierte Shellanwendung. Wenn die Anwendung ausgeführt wird, werden die Registrierungs Einstellungen in der folgenden Reihenfolge definiert:  
  
 Wenn die Anwendung ausgeführt wird, werden die Registrierungs Einstellungen in der folgenden Reihenfolge definiert:  
  
1. Der Registrierungsschlüssel für die Anwendung wird erstellt.  
  
2. Die Registrierung wird aus der pkgdef-Datei der Anwendung aktualisiert, indem die angegebenen Schlüssel und Einträge definiert werden.  
  
3. Für jedes Paket, das Teil Ihrer Anwendung ist, wird die Registrierung aus der pkgdef-Datei des Pakets aktualisiert. Jedes Paket wird in der pkgdef-Datei der Anwendung durch den $RootKey $ \packages \\ {*vspackageguid*}-Schlüssel für das Paket definiert.  
  
4. Die Registrierung wird aus der Datei "appenvconfig. pkgdef" und "baseconfig. pkgdef" im *Visual Studio SDK-Installationspfad*\common7\ide\shellextensions\platform Directory aktualisiert. Diese Dateien sind Teil von Visual Studio und auch Teil des verteilbaren Pakets für Visual Studio Shell (isolierter Modus).  
  
5. Die Registrierung wird aus der pkgundef-Datei der Anwendung aktualisiert, indem die angegebenen Schlüssel und Einträge entfernt werden.  
  
## <a name="run-time-settings"></a>Lauf Zeit Einstellungen  
 Wenn ein Benutzer die isolierte Shellanwendung startet, ruft er den Start Einstiegspunkt der Visual Studio-Shell auf. Anwendungseinstellungen werden beim Starten der Anwendung wie folgt definiert:  
  
1. Die Visual Studio-Shell überprüft die Anwendungs Registrierung auf bestimmte Schlüssel. Wenn die Einstellung für einen Schlüssel im-Befehl des Start Einstiegs Punkts angegeben wird, überschreibt dieser Wert den Wert in der Registrierung.  
  
2. Wenn weder die Registrierung noch der Einstiegspunkt Parameter den Wert einer Einstellung angibt, wird der Standardwert für die Einstellung verwendet.  
  
   Wenn ein Benutzer die Anwendung über die Befehlszeile startet, werden alle Befehls Zeilenschalter an die Visual Studio-Shell übermittelt, die Sie auf die gleiche Weise behandelt wie bei "Debug". Weitere Informationen zu devenv-Switches finden Sie unter [devenv-Befehls Zeilenschalter](../ide/reference/devenv-command-line-switches.md) und [devenv-Befehls Zeilenschalter für die VSPackage-Entwicklung](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Weitere Informationen zum Registrieren eines Pakets für Befehls Zeilenschalter finden Sie unter [Hinzufügen von Befehls zeilenschaltern](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Der Start Einstiegspunkt  
 Die Appenvstub.dll Datei enthält Einstiegspunkte für den Zugriff auf die isolierte Shell. Wenn die Anwendung gestartet wird, ruft Sie den Start Einstiegspunkt der Appenvstub.dll auf.  
  
 Sie können das Verhalten der Anwendung ändern, indem Sie den Wert des letzten Parameters ändern, der an den Start Einstiegspunkt übergeben wird. Weitere Informationen finden Sie unter [Parameter für isolierte Shell-Einstiegspunkte (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Die. Vsct-Datei  
 Mit der vsct-Datei können Sie angeben, welche standardmäßigen Visual Studio-Benutzeroberflächen Elemente in der Anwendung verfügbar sind. Weitere Informationen finden Sie unter [. Vsct-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Die. Pkgundef-Datei  
 Wenn die Anwendung auf einem Computer installiert ist, auf dem Visual Studio bereits installiert ist, wird eine Kopie der Visual Studio-Registrierungseinträge für die Anwendung erstellt. Standardmäßig verwendet die Anwendung VSPackages, die bereits auf dem Computer installiert sind. Mithilfe der pkgundef-Datei können Sie Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen aus der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Mithilfe der pkgundef-Datei können Sie Registrierungseinträge ausschließen, um bestimmte Elemente der Visual Studio-Shell oder Erweiterungen aus der Anwendung zu entfernen. Weitere Informationen finden Sie unter [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Die Gruppe von Paket-GUIDs, die Sie ausschließen können, ist unter [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)aufgeführt.  
  
## <a name="the-pkgdef-file"></a>Die. Pkgdef-Datei  
 Mithilfe der pkgdef-Datei können Sie Registrierungseinträge für die Anwendung definieren, die festgelegt werden, wenn die Anwendung installiert wird. Eine Beschreibung der pkgdef-Datei und eine Liste der Registrierungseinträge, die von der Visual Studio-Shell verwendet werden, finden Sie unter [. Pkgdef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ersatz Zeichenfolgen  
 Die in den pkgdef-und pkgundef-Dateien verwendeten Ersetzungs Zeichenfolgen werden in Ersetzungs Zeichenfolgen aufgelistet, die [in verwendet werden. Pkgdef und. Pkgundef-Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Weitere Einstellungen  
 Wenn die isolierte Shellanwendung von Microsoft.VisualStudio.GraphModel.dll abhängig ist, müssen Sie der config-Datei Ihrer isolierten Shellanwendung die folgende Bindungs Umleitung hinzufügen:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

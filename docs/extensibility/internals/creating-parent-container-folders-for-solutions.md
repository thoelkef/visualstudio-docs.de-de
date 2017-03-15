---
title: "Erstellen von &#252;bergeordneten Containerordnern f&#252;r L&#246;sungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erstellen von übergeordneten Container-Projektmappen"
  - "Source Control-Plug-ins übergeordneten Container erstellt."
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Erstellen von &#252;bergeordneten Containerordnern f&#252;r L&#246;sungen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der Version 1.2 des Quellcodeverwaltungs\-Plug\-In APIs, kann ein Benutzer ein einzelnes Stammelement quellcodeverwaltungs Ziel für alle Webprojekte in der Projektmappe angeben.  Dieser einzelne Stamm ist ein einheitlicher Stamm \(SUR einen super\) bezeichnet.  
  
 In der Version 1.1 des Quellcodeverwaltungs\-Plug\-In API, wenn der Benutzer eine multiproject Projektmappe zur Quellcodeverwaltung hinzugefügt hat, wird der Benutzer aufgefordert, ein Webprojekt jedes Ziel für Quellcodeverwaltung festlegen.  
  
## Neue Funktions\-Flags  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## Neue Funktionen  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE stellt nahezu immer einen SUR\-Ordner erstellt, wenn eine Projektmappe zur Quellcodeverwaltung hinzufügen.  Insbesondere bleibt sie so in den folgenden Fällen:  
  
-   Das Projekt ist eine Dateifreigabe Webprojekt.  
  
-   Es gibt verschiedene Laufwerk für das Projekt und die Projektmappe.  
  
-   Es gibt verschiedene Freigabe für das Projekt und die Projektmappe.  
  
-   Projekte einzeln hinzugefügt wurden \(in einem unterliegender Quellcodeverwaltung Projektmappe\).  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Es wird empfohlen, dass der Name für den SUR\-Ordner derselbe wie der Projektmappenname ohne Erweiterung ist.  In der folgenden Tabelle wird das Verhalten in den beiden Versionen zusammengefasst.  
  
|Feature|Plug\-In API Version 1.1 tSource Steuerelements|Version 1.2 des Quellcodeverwaltungs\-Plug\-In\-API|  
|-------------|-----------------------------------------------------|---------------------------------------------------------|  
|Fügen Sie der Projektmappe hinzufügen SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|Fügen Sie dem Projekt unterliegender Quellcodeverwaltung Projektmappe hinzu|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio wird davon ausgegangen, dass eine Projektmappe ein unmittelbares Unterelement des SUR ist.|  
  
## Beispiele  
 Die folgende Tabelle enthält zwei Beispiele.  In beiden Fällen wird der Speicherort des Ziels für einen Benutzer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für die Projektmappe unter Quellcodeverwaltung aufgefordert, bis *user\_choice* als Ziel angegeben ist. Wenn das user\_choice angegeben wird, werden die Projektmappe und zwei Projekte hinzugefügt, ohne den Benutzer zur Eingabe aufzufordern auf Quellcodeverwaltung.  
  
|Projektmappe|Klicken Sie auf Speicherorte auf einem Datenträger|standardmäßigen Struktur der Datenbank|  
|------------------|--------------------------------------------------------|--------------------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\\Solutions\\sln1<br /><br /> C:\\Inetpub\\wwwroot\\Web1<br /><br /> wwwroot$ \\. \\ \\ Server \\ web2|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\\Solutions\\sln1<br /><br /> D:\\Inetpub\\wwwroot\\Web1<br /><br /> C:\\solutions\\sln1\\Win1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 Der SUR\-Ordner und Unterordner werden erstellt, unabhängig davon, ob der Vorgang abgebrochen wurde oder aufgrund eines Fehlers fehlgeschlagen ist.  Sie werden nicht automatisch im Löschen oder in Fehlerzuständen entfernt.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] führt zu Verhalten der Version 1.1, wenn das Quellcodeverwaltungs\-Plug\-In nicht `SCC_CAP_CREATESUBPROJECT` und Flags für `SCC_CAP_GETPARENTPROJECT`\-Funktion zurückgibt.  Darüber hinaus können Benutzer von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auswählen, um das Verhalten der Version 1.1 wiederherzustellen, indem sie den Wert der folgenden Schlüssel zum steht " dword: 00000001:  
  
 \[HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ SourceControl\] " DoNotCreateSolutionRootFolderInSourceControl „\=dword: 00000001  
  
## Siehe auch  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
---
title: Erstellen von übergeordneten Container Ordnern für Projektmappen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196928"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Erstellen von übergeordneten Containerordnern für Projektmappen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der Quellcodeverwaltungs-Plug-in-API-Version 1,2 kann ein Benutzer ein einzelnes Quell Code Verwaltungs Ziel für alle Webprojekte in der Projekt Mappe angeben. Dieser einzelne Stamm wird als Super Unified root (sur) bezeichnet.  
  
 Wenn der Benutzer in der Quellcodeverwaltungs-Plug-in-API Version 1,1 eine Projekt Mappe mit mehreren Projekten zur Quell Code Verwaltung hinzugefügt hat, wurde der Benutzer aufgefordert, ein Quell Code Verwaltungs Ziel für jedes Webprojekt anzugeben.  
  
## <a name="new-capability-flags"></a>Neue funktionsflags  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE erstellt beim Hinzufügen einer Projekt Mappe zur Quell Code Verwaltung fast immer einen sur-Ordner. Dies geschieht insbesondere in den folgenden Fällen:  
  
- Das Projekt ist ein Dateifreigabe-Webprojekt.  
  
- Es gibt verschiedene Laufwerke für das Projekt und die Projektmappendatei.  
  
- Es gibt verschiedene Freigaben für das Projekt und die Projektmappendatei.  
  
- Projekte wurden separat hinzugefügt (in einer Lösung für die Quell Code Verwaltung).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Es wird empfohlen, dass der Name des Ordners "sur" mit dem Projektmappennamen ohne Erweiterung identisch ist. In der folgenden Tabelle wird das Verhalten in den beiden Versionen zusammengefasst.  
  
|Funktion|TSource-Steuerelement-Plug-in-API, Version 1,1|Quellcodeverwaltungs-Plug-in-API, Version 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Lösung zu SCC hinzufügen|Sccinitialize ()<br /><br /> Sccgetprojpath ()<br /><br /> Sccgetprojpath ()<br /><br /> Sccopumproject ()|Sccinitialize ()<br /><br /> Sccgetprojpath ()<br /><br /> Scckreatesubproject ()<br /><br /> Scckreatesubproject ()<br /><br /> Sccopumproject ()|  
|Projekt der Projekt Mappe zur Quell Code Verwaltung hinzufügen|Sccgetprojpath ()<br /><br /> OpenProject ()|Sccgetparametprojectpath ()<br /><br /> Sccoperproject () **Hinweis:**  Visual Studio geht davon aus, dass eine Projekt Mappe ein direktes untergeordnetes Element der sur ist.|  
  
## <a name="examples"></a>Beispiele  
 In der folgenden Tabelle sind zwei Beispiele aufgeführt. In beiden Fällen wird der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzer zur Eingabe eines Zielspeicher Orts für die Lösung unter Quell Code Verwaltung aufgefordert, bis die  *user_choice* als Ziel angegeben wird. Wenn die user_choice angegeben wird, werden die Projekt Mappe und zwei Projekte hinzugefügt, ohne dass der Benutzer zur Eingabe von Quell Code Verwaltungs Zielen aufgefordert wird.  
  
|Projekt Mappe enthält|Auf Speicherorten|Daten Bank Standardstruktur|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Web1<br /><br /> Web2|C:\solutions\sln1<br /><br /> C:\inetpub\wwwroot\web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/web1<br /><br /> $/*user_choice*/web2|  
|sln1. sln<br /><br /> Web1<br /><br /> Win1|C:\solutions\sln1<br /><br /> D:\inetpub\wwwroot\web1<br /><br /> C:\solutions\sln1\win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 Der Ordner "sur" und die Unterordner werden unabhängig davon erstellt, ob der Vorgang aufgrund eines Fehlers abgebrochen wurde oder fehlschlägt. Sie werden nicht automatisch in Abbruch-oder Fehlerzuständen entfernt.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]hat standardmäßig das Verhalten von Version 1,1, wenn das Quellcodeverwaltungs-Plug-in keine `SCC_CAP_CREATESUBPROJECT` -und-funktionsflags zurückgibt `SCC_CAP_GETPARENTPROJECT` Außerdem können Benutzer von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auswählen, das Verhalten von Version 1,1 wiederherzustellen, indem Sie den Wert des folgenden Schlüssels auf DWORD festlegen: 00000001:  
  
 [HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] "Donotkreatesolutionrootfolderinsourcecontrol" = DWORD: 00000001  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

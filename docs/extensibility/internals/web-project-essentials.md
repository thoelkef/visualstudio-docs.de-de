---
title: Web-Projekt Essentials | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ac781256ee78becf3b0cfdffbbec6f0c6bc30225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="web-project-essentials"></a>Web Project Essentials
Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung zu erstellen, die verfügt der intelligenten Webseiten. Eine intelligente Webseite wurde serverseitigen Code, der die Webseite bedarfsgesteuert gerendert wird.  
  
 Mit herkömmlichen Programmiersprachen wie [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], können Sie intelligente Webseiten zum Erfassen und Verarbeiten von Informationen von einem Benutzer, in einer Datenbank zu speichern und usw. erstellen.  
  
-   Der Code-Behind-Modells Webseiten, auf denen der ASPX-Datei-Erweiterung ASMX oder abhängige Quellcodedateien zugeordnet. Z. B. möglicherweise hello.aspx der abhängigen Datenquellen Code Datei hello.aspx.cs.  
  
-   Die serverseitigen Code eine intelligente Webseite zugeordnet wird in eine ausführbare Datei kompiliert, die in den Ordner der Website "/ bin" befindet.  
  
-   Zusätzliche Quellcodedateien, z. B. Hilfsklassen, die nicht mit einer bestimmten Webseite verknüpft sind befinden sich im Ordner "App_Code Web Site".  
  
    -   Ein Website-Projekt (WSP) wird eine ausführbare Datei für jede intelligenten Webseite generiert. Zusätzliche ausführbare Dateien werden von alle Quellcodedateien im Ordner "App_Code" generiert.  
  
    -   Ein Webanwendungsprojekt (WAP) erzeugt eine einzelne ausführbare Datei, die den Code für alle intelligenten Webseiten als auch alle Dateien im Ordner "App_Code" kombiniert.  
  
-   Die Projektmappendatei für ein Webprojekt ist separat von der Website selbst gespeichert. Standardmäßig befinden sich Projektmappendateien am \Documents and Settings\\*Ihr Konto*\My Dokumente\\*\<Visual Studio ### >*\Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Wenn Sie die Projektmappendatei mit der Website beibehalten möchten, verschieben Sie sie nur vorhanden, und öffnen Sie es erneut.  
  
-   Wenn Sie eine Website, die keine Projektmappendatei in Visual Studio verfügt öffnen, wird eine neue Projektmappendatei für sie automatisch generiert.  
  
-   Webprojekte haben keine Projektdateien. Projektinformationen ist in der Projektmappendatei, die Datei "Web.config" und an anderer Stelle gespeichert.  
  
-   Globale Eigenschaften automatisch zu einem Webprojekt hinzufügen erstellt eine Speicherdatei im Projektmappenordner Web Project.  
  
-   Eine intelligente Webseite kann eine serverseitige Programmiersprache zugeordnet werden, mithilfe der Seitendirektive oder \<Skript Runat = "Server" > Tag.  
  
-   Darüber hinaus können Webseiten eine beliebige Anzahl von clientseitigen Skripts Blöcke in jeder Skriptsprache geschrieben haben.  
  
-   Ein Website-Projektsystem wird durch Hinzufügen von Projekt- und Elementvorlagen und Registrierung für Azure implementiert die [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt.  
  
-   Ein WAP-System wird als ein Projektuntertyp, der so genannte eine Projektkonfiguration implementiert. Die [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt ist flavored, von der WAP-Untertyp, der WAP-System zu erstellen. Weitere Informationen zum Projekt Untertypen, finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
-   Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache Ihrer Wahl. Die serverseitige Sprache wird die enthaltene Sprache aufgerufen. Um eine eigenständige Sprache unterstützen, muss die Web-Projektsystem implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstellen-Betriebssystemfamilie.  
  
    -   Zur Unterstützung von eigenständigen Language in einem Editor muss die HTML-Sprachdienst Anzeigen von eigenständigen Sprachcode für einen eigenständigen Sprachdienst verzögern.  
  
    -   Fehler-Marker (rote Unterstreichung) müssen immer im Code-Editor primären Puffer erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Webprojekte](../../extensibility/internals/web-projects.md)
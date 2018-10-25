---
title: Web-Projekt Essentials | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb69eeb701ed5ce24259d203c0320c2635c96e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934521"
---
# <a name="web-project-essentials"></a>Grundlagen von Webprojekten
Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung erstellen, die intelligente Webseiten. Eine intelligente Webseite hat serverseitigem Code, der die Webseite bedarfsgesteuert gerendert wird.  
  
 Mit herkömmlichen Programmiersprachen wie [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], können Sie intelligente Webseiten zum Sammeln und Verarbeiten von Informationen von einem Benutzer, in einer Datenbank zu speichern und usw. erstellen.  
  
- Der Code-Behind-Modells von Webseiten, die die Datei Erweiterung ASPX ASMX oder abhängige Quellcodedateien zugeordnet. Z. B. möglicherweise hello.aspx die Quelle von abhängiger Code Datei hello.aspx.cs.  
  
- Der serverseitige Code eine intelligente Webseite zugeordnet wird in eine ausführbare Datei kompiliert, die in den Ordner der Website "/ bin" befindet.  
  
- Zusätzliche Quellcodedateien, z. B. Hilfsklassen, die nicht mit einer bestimmten Webseite verknüpft sind befinden sich in den Ordner der Website kann.  
  
  -   Ein Websiteprojekt (WSP) generiert eine ausführbare Datei für jedes smart-Webseite. Weitere ausführbare Dateien werden von alle Quellcodedateien im Ordner "kann" generiert.  
  
  -   Ein Webanwendungsprojekt (WAP) erzeugt eine einzelne ausführbare Datei, die den Code für alle smart Webseiten als auch alle Quelldateien im Ordner "kann" kombiniert.  
  
- Die Projektmappendatei für ein Webprojekt befindet sich unabhängig von der Website selbst. Standardmäßig befinden sich Projektmappendateien unter \Documents and Settings\\*Ihrkonto*\My Dokumente\\*\<Visual Studio ### >* \Projects\\ *YourWebSite*.  
  
  > [!NOTE]
  >  Wenn Sie die Projektmappendatei mit der Website beibehalten möchten, es verschieben und öffnen Sie es erneut.  
  
- Wenn Sie eine Website, die keine Projektmappendatei in Visual Studio verfügt öffnen, wird eine neue Projektmappendatei automatisch für sie generiert.  
  
- Webprojekte haben keine Projektdateien. Projektinformationen werden in die Projektmappendatei, die Datei "Web.config" und an anderer Stelle gespeichert.  
  
- Automatisches Hinzufügen von globalen Eigenschaften mit einem Webprojekt erstellt eine Speicherdatei in den Projektmappenordner der Web-Projekt.  
  
- Eine intelligente Webseite kann mithilfe der Page-Direktive einer serverseitigen Programmiersprache zugeordnet werden oder die \<Skript Runat = "Server" > Tag.  
  
- Darüber hinaus können Webseiten eine beliebige Anzahl von Client-Side scripting Blöcke in jeder Skriptsprache geschrieben haben.  
  
- Ein Website-Projektsystem wird durch Hinzufügen von Projekt- und Elementvorlagen und Registrierung implementiert die [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt.  
  
- Ein WAP-System wird als einem Projektuntertyp, die so genannte ein Projektkonfiguration implementiert. Die [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt ist flavored, durch den WAP-Untertyp, der WAP-System zu erstellen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
- Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache. Die serverseitigen Sprache wird die enthaltende Sprache bezeichnet. Um einer enthaltenen Sprache zu unterstützen, muss die Web-Projektsystem implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Familie von Schnittstellen.  
  
  -   Um die enthaltende Sprache in einem Editor zu unterstützen, muss HTML-Sprachdiensts verzögern enthaltenen Sprachcode an einen Dienst für die enthaltende Sprache angezeigt.  
  
  -   Fehlermarker (rote, wellenförmige Unterstreichung) müssen immer im primären Puffer des Code-Editor erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Webprojekte](../../extensibility/internals/web-projects.md)
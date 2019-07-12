---
title: Web-Projekt Essentials | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825616"
---
# <a name="web-project-essentials"></a>Grundlagen von Webprojekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung erstellen, die intelligente Webseiten. Eine intelligente Webseite hat serverseitigem Code, der die Webseite bedarfsgesteuert gerendert wird.  
  
 Mit herkömmlichen Programmiersprachen wie [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)], können Sie intelligente Webseiten zum Sammeln und Verarbeiten von Informationen von einem Benutzer, in einer Datenbank zu speichern und usw. erstellen.  
  
- Der Code-Behind-Modells von Webseiten, die die Datei Erweiterung ASPX ASMX oder abhängige Quellcodedateien zugeordnet. Z. B. möglicherweise hello.aspx die Quelle von abhängiger Code Datei hello.aspx.cs.  
  
- Der serverseitige Code eine intelligente Webseite zugeordnet wird in eine ausführbare Datei kompiliert, die in den Ordner der Website "/ bin" befindet.  
  
- Zusätzliche Quellcodedateien, z. B. Hilfsklassen, die nicht mit einer bestimmten Webseite verknüpft sind befinden sich in den Ordner der Website kann.  
  
  - Ein Websiteprojekt (WSP) generiert eine ausführbare Datei für jedes smart-Webseite. Weitere ausführbare Dateien werden von alle Quellcodedateien im Ordner "kann" generiert.  

  - Ein Webanwendungsprojekt (WAP) erzeugt eine einzelne ausführbare Datei, die den Code für alle smart Webseiten als auch alle Quelldateien im Ordner "kann" kombiniert.  
  
- Die Projektmappendatei für ein Webprojekt befindet sich unabhängig von der Website selbst. Standardmäßig befinden sich Projektmappendateien unter \Documents and Settings\\*Ihrkonto*\My Dokumente\\ *\<Visual Studio ### >* \Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    > Wenn Sie die Projektmappendatei mit der Website beibehalten möchten, es verschieben und öffnen Sie es erneut.  
  
- Wenn Sie eine Website, die keine Projektmappendatei in Visual Studio verfügt öffnen, wird eine neue Projektmappendatei automatisch für sie generiert.  
  
- Webprojekte haben keine Projektdateien. Projektinformationen werden in die Projektmappendatei, die Datei "Web.config" und an anderer Stelle gespeichert.  
  
- Automatisches Hinzufügen von globalen Eigenschaften mit einem Webprojekt erstellt eine Speicherdatei in den Projektmappenordner der Web-Projekt.  
  
- Eine intelligente Webseite kann mithilfe der Page-Direktive einer serverseitigen Programmiersprache zugeordnet werden oder die \<Skript Runat = "Server" > Tag.  
  
- Darüber hinaus können Webseiten eine beliebige Anzahl von Client-Side scripting Blöcke in jeder Skriptsprache geschrieben haben.  
  
- Ein Website-Projektsystem wird durch Hinzufügen von Projekt- und Elementvorlagen und Registrierung implementiert die [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] Projekt.  
  
- Ein WAP-System wird als einem Projektuntertyp, die so genannte ein Projektkonfiguration implementiert. Die [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] Projekt ist flavored, durch den WAP-Untertyp, der WAP-System zu erstellen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
- Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache. Die serverseitigen Sprache wird die enthaltende Sprache bezeichnet. Um einer enthaltenen Sprache zu unterstützen, muss die Web-Projektsystem implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Familie von Schnittstellen.  
  
  - Um die enthaltende Sprache in einem Editor zu unterstützen, muss HTML-Sprachdiensts verzögern enthaltenen Sprachcode an einen Dienst für die enthaltende Sprache angezeigt.  

  - Fehlermarker (rote, wellenförmige Unterstreichung) müssen immer im primären Puffer des Code-Editor erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Webprojekte](../../extensibility/internals/web-projects.md)

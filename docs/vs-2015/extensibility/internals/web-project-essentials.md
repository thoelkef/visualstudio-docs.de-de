---
title: Essentials-Webprojekt | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825616"
---
# <a name="web-project-essentials"></a>Grundlagen von Webprojekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung zu erstellen, die über intelligente Webseiten verfügt. Eine intelligente Webseite verfügt über serverseitigen Code, der die Webseite bei Bedarf rendert.  
  
 Mithilfe von herkömmlichen Programmiersprachen, wie z. b. [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)] , können Sie intelligente Webseiten erstellen, um Informationen von einem Benutzer zu erfassen und zu verarbeiten, in einer Datenbank zu speichern usw.  
  
- Das Code Behind-Modell verknüpft abhängige Quell Code Dateien mit Webseiten, die die Dateierweiterung ". aspx" oder ". asmx" aufweisen. Beispielsweise kann "Hello. aspx" die abhängige Quell Code Datei "Hello.aspx.cs" aufweisen.  
  
- Der serverseitige Code, der einer intelligenten Webseite zugeordnet ist, wird in eine ausführbare Datei kompiliert, die sich im Ordner "Website"/bin "" befindet.  
  
- Zusätzliche Quell Code Dateien, z. b. Hilfsklassen, die keiner bestimmten Webseite zugeordnet sind, befinden sich im Ordner Website/App_Code.  
  
  - Ein Website Projekt (WSP) generiert eine ausführbare Datei für jede intelligente Webseite. Zusätzliche ausführbare Dateien werden aus beliebigen Quell Code Dateien im Ordner/App_Code generiert.  

  - Ein Webanwendungs Projekt (WAP) erzeugt eine einzelne ausführbare Datei, die den Code für alle intelligenten Webseiten sowie alle Quelldateien im Ordner/App_Code kombiniert.  
  
- Die Projektmappendatei für ein Webprojekt befindet sich separat von der Website selbst. Standardmäßig befinden sich Projektmappendateien unter \Documents und Settings \\ *YourAccount*\My Documents \\ *\<Visual Studio ####>* \projects \\ *yourwebsite*.  
  
    > [!NOTE]
    > Wenn Sie die Projektmappendatei auf der Website aufbewahren möchten, verschieben Sie Sie einfach dorthin, und öffnen Sie Sie erneut.  
  
- Wenn Sie eine Website öffnen, die keine Projektmappendatei in Visual Studio enthält, wird automatisch eine neue Projektmappendatei generiert.  
  
- Webprojekte haben keine Projektdateien. Die Projektinformationen werden in der Projektmappendatei, in der web.config-Datei und an anderer Stelle gespeichert.  
  
- Durch das Hinzufügen globaler Eigenschaften zu einem Webprojekt wird automatisch eine Speicherdatei im Projektmappen-Ordner des Webprojekts erstellt.  
  
- Eine intelligente Webseite kann mithilfe der Page-Direktive oder des-Tags einer serverseitigen Programmiersprache zugeordnet werden \<script runat="server"> .  
  
- Darüber hinaus können Webseiten über eine beliebige Anzahl von Client seitigen Skript Blöcken verfügen, die in einer beliebigen Skriptsprache geschrieben wurden.  
  
- Ein Website Projekt System wird implementiert, indem Projekt-und Element Vorlagen und die Registrierung für das Projekt hinzugefügt werden [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] .  
  
- Ein WAP-System wird als Projekt Untertyp implementiert, auch als Projekt Konfiguration bezeichnet. Das [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] Projekt wird vom WAP-Untertyp zum Erstellen des WAP-Systems hinzu gestellt. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
- Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache. Die serverseitige Sprache wird als enthaltene Sprache bezeichnet. Um eine enthaltene Sprache zu unterstützen, muss das Webprojekt System die-Schnittstelle implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  
  
  - Um die enthaltene Sprache in einem Editor zu unterstützen, muss der HTML-Sprachdienst die Anzeige von enthaltendem Sprachcode in einem enthaltenen Sprachdienst verzögern.  

  - Fehler Marker (rote Wellenlinien) sollten immer im primären Puffer des Code-Editors erstellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Webprojekte](../../extensibility/internals/web-projects.md)

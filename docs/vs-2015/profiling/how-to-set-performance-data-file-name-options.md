---
title: 'Vorgehensweise: Dateinamenoptionen für Profilerstellungsdaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3d513010b94c61e09f8bda6a9fb3074ba949bdd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760413"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Vorgehensweise: Dateinamenoptionen für Profilerstellungsdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig speichern Sie eine Profilerstellungs-Datendatei (.vsp) mithilfe der folgenden Syntax:  
  
 *Path\VSP-File\YYMMDD(N)* **.vsp**  
  
 Sie können auf der Seite „Allgemein“ im Dialogfeld „Eigenschaften“ für die Leistungssitzung jeden Namensparameter ändern.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|||  
|-|-|  
|*Pfad*|Das Verzeichnis mit dem Bericht. Der Standardspeicherort ist der Projektmappenordner oder der Standardspeicherort für Projekte und Projektmappen des Benutzers.|  
|*VSP-Datei*|Der Name der Profilerstellungs-Datendatei. Der Standardname ist der Name der Projektmappe oder der ausführbaren Datei, für die ein Profil erstellt wird.|  
|*JJMMTT*|Ein Datumsstempel, der Jahr, Monat und Tag anzeigt, an dem die Profilerstellungsdaten gesammelt wurden.|  
|*(N)*|Wenn mehr als eine Profilerstellungsdatendatei vorhanden ist, wird dem Dateinamen eine inkrementierte Zahl in Klammern hinzugefügt.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>So ändern Sie die Benennungssyntax der Profilerstellungs-Datendateien einer Leistungssitzung  
  
1.  Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung und anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Allgemein**.  
  
3.  Ändern Sie unter **Bericht** eine der folgenden Einstellungen:  
  
    |||  
    |-|-|  
    |**Berichtsspeicherort**|Geben Sie ein Verzeichnis zum Speichern der Profilerstellungs-Datendateien an.|  
    |**Berichtsname**|Geben Sie einen Basisnamen für die Dateien an.|  
    |**Neue Berichte automatisch zur Sitzung hinzufügen**|Wählen Sie das Kontrollkästchen aus, um die Datendatei der Leistungssitzung automatisch hinzuzufügen.|  
    |**Generierte Berichte mit inkrementeller Nummer versehen**|Wählen Sie das Kontrollkästchen aus, um eine inkrementelle Nummer an den Dateinamen hinzuzufügen, wenn mehr als eine Datei mit demselben Namen vorhanden ist. Deaktivieren Sie das Kontrollkästchen, um eine vorhandene Datei zu überschreiben.|  
    |**Zeitstempel für die Nummer verwenden**|Wählen Sie das Kontrollkästchen aus, um dem Dateinamen einen Datumsstempel hinzuzufügen.|

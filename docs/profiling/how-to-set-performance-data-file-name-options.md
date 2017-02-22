---
title: "Gewusst wie: Dateinamenoptionen f&#252;r Profilerstellungsdaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Dateinamenoptionen f&#252;r Profilerstellungsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig speichern Sie mit der folgenden Syntax eine Profilerstellungs\-Datendatei \(.vsp\):  
  
 *Path\\VSP\-File\\YYMMDD\(N\)* **.vsp**  
  
 Sie können auf der Seite Allgemein des Eigenschaftendialogfelds für die Leistungssitzung jeden beliebigen Namensparameter ändern.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
|||  
|-|-|  
|*Path*|Das Verzeichnis, das den Bericht enthält.  Der Standardspeicherort ist der Projektmappenordner oder der Standardspeicherort der Projekte und Projektmappen des Benutzers.|  
|*VSP\-File*|Der Name der Profilerstellungs\-Datendatei.  Der Standardname ist der Name der Projektmappe oder der ausführbaren Datei, die profiliert wird.|  
|*YYMMDD*|Ein Datumsstempel, der das Jahr, den Monat und den Tag anzeigt, an dem die Profilerstellungsdaten gesammelt wurden.|  
|*\(N\)*|Wenn es mehr als eine Profilerstellungs\-Datendatei gibt, wird dem Dateinamen zwischen Klammern eine inkrementierte Zahl hinzugefügt.|  
  
### So ändern Sie die Namenssyntax der Profilerstellungs\-Datendateien einer Leistungssitzung  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Allgemein**.  
  
3.  Ändern Sie unter **Bericht** eine der folgenden Einstellungen:  
  
    |||  
    |-|-|  
    |**Berichtsspeicherort**|Geben Sie ein Verzeichnis an, um die Profilerstellungs\-Datendateien zu speichern.|  
    |**Berichtsname**|Geben Sie einen Basisnamen für die Dateien an.|  
    |**Neue Berichte automatisch zur Sitzung hinzufügen**|Aktivieren Sie das Kontrollkästchen, um der Leistungssitzung die Datendatei automatisch hinzuzufügen.|  
    |**Generierte Berichte mit inkrementeller Nummer versehen**|Aktivieren Sie dieses Kontrollkästchen, um dem Dateinamen eine inkrementelle Nummer hinzuzufügen, wenn mehr als eine Datei mit dem gleichen Namen vorhanden ist.  Deaktivieren Sie das Kontrollkästchen, um eine vorhandene Datei zu überschreiben.|  
    |**Timestamp für Nummer verwenden**|Aktivieren Sie das Kontrollkästchen, um dem Dateinamen einen Datumsstempel hinzuzufügen.|
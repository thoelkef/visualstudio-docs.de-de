---
title: "Speichern von symbolischen Informationen mittels Profilerstellungsdatendateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Packsymbols, in Berichten für Profilerstellungstools"
  - "Profilerstellungstools, Packsymbols"
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Speichern von symbolischen Informationen mittels Profilerstellungsdatendateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie die integrierte Entwicklungsumgebung \(IDE\) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Analysieren von Dateien verwenden und beabsichtigen, die VSP\-Datei auf einen anderen Computer zu verschieben, müssen die Einstellungen des Leistungsberichtsprojekts so festgelegt werden, dass Symbole in der Berichtsdatei gespeichert oder *serialisiert* werden.  Dadurch erhöht sich die Größe einer Berichtsdatei.  Die Serialisierung von Symbolen ist aus zwei Gründen notwendig:  
  
-   Zum Einbetten von Codesymbolen in einen Leistungsbericht, bevor die Position der Zielassemblys im temporären Speicher verloren geht.  
  
-   Damit Symbole erhalten bleiben, sodass der Leistungsbericht von dem für die Profilerstellung verwendeten Computer portiert werden kann und dieselben Informationen ausgibt, wenn der Bericht zur Analyse auf einem anderen Computer geöffnet wird, der möglicherweise über abweichende Symbole verfügt.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Sie können Symbole über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE oder an der Befehlszeile serialisieren:  
  
-   Um Symbole in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE zu serialisieren, zeigen Sie in der Menüleiste auf **Extras**, und klicken Sie dann auf **Optionen**.  Wählen Sie im Fenster **Optionen** die Option **Leistungstools** aus, und aktivieren Sie dann das Kontrollkästchen **Symbolinformationen automatisch serialisieren**.  
  
-   PACKSYMBOLS ist die entsprechende Befehlszeilenoption, wenn Sie Berichtsdateien speichern.  Um Symbole zu serialisieren, geben Sie vsperfreport \/summary:all \/packsymbols filename.vsp ein.  
  
## Beheben von Symbolproblemen  
 Wenn im eigenen Code keine Symbole zu sehen sind, gibt es einige allgemeine Lösungsmöglichkeiten:  
  
-   Führen Sie vsperfreport \/debugsympath an einer Befehlszeile aus, um eine vollständige Liste der Speicherorte anzuzeigen, unter denen Symbolinformationen von Profilerkomponenten geladen werden, und um festzustellen, ob die verwendeten Symboldateien mit den von Ihrem Projekt verwendeten Dateien übereinstimmen.  
  
-   Achten Sie darauf, dass vsperfreport mit dem \/PACKSYMBOLS\-Flag ausgeführt wird bzw. dass Sie in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE in den allgemeinen Optionen für den Leistungs\-Explorer die Option zum Serialisieren von Symbolinformationen aktiviert haben.  
  
-   Wenn Typdaten erfasst wurden, fügen Sie \/SUMMARY:TYPE in die vsperfreport\-Befehlszeile ein.  
  
 Wenn Sie keine Symbole von Windows oder anderen Microsoft\-Programmen sehen:  
  
-   Stellen Sie sicher, dass Sie den Pfad zum Windows\-Symbolcache festgelegt haben.  Führen Sie einen der folgenden Schritte aus, um den Symbolcachepfad festzulegen:  
  
    -   Legen Sie die Debugger\-Symboloption \>in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \- IDE auf den richtigen Pfad fest.  
  
    -   Fügen Sie die \- symbolpath\-Option zur VSPerfReport\-Befehlszeile hinzu, um die Symbole einzuschließen.  
  
-   Wenn in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] keine Symbole angezeigt werden, sollten Sie sicherstellen, dass der Symbolserver ordnungsgemäß für den ASP\-Server eingerichtet wurde.  
  
## Erneutes Packen von Symbolen  
 Wenn Sie Symbole erneut in einen Bericht packen möchten, können Sie dazu das Befehlszeilentool VsPerfReport verwenden.  Verwenden Sie die folgenden Befehlszeilen:  
  
 VsPerfReport \- clearpackedsymbols Dateiname.vsp  
  
 VsPerfReport \-packsymbols \-summary:all Dateiname.vsp  
  
## Siehe auch  
 [Speichern und Exportieren von Daten aus Leistungstools](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
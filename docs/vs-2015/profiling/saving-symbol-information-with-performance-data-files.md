---
title: Speichern von symbolischen Informationen mittels Leistungsdatendateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160299"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Speichern von symbolischen Informationen mittels Profilerstellungsdatendateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie das Integrated Development Environment (IDE) von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden, um Dateien zu analysieren, und Ihre VSP-Datei auf einen anderen Computer verschieben möchten, müssen Sie die Leistungsprojekteinstellungen festlegen, um Symbol in Ihrer Berichtsdatei zu speichern oder zu *serialisieren*. Dadurch vergrößert sich die Berichtsdatei. Die Serialisierung von Symbolen ist aus zwei Gründen erforderlich:  
  
- Einbetten von Codesymbolen in einen Leistungsbericht, bevor die Zielassemblys an ihrem Speicherort im temporären Speicher verloren gehen.  
  
- Beibehalten von Symbolen, sodass der Leistungsbericht vom profilierten Computer portierbar ist und die gleichen Informationen ausgibt, wenn der Bericht zur Analyse auf einem anderen Computer geöffnet wird, der andere Symbole haben kann.  
  
  **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Sie können Symbole vom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE oder von der Befehlszeile serialisieren;  
  
- Zum Serialisieren von Symbolen im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE zeigen Sie auf **Extras** in der Menüleiste, und klicken Sie dann auf **Optionen**. Wählen Sie im Fenster **Optionen****Leistungstools** aus, und aktivieren Sie das Kontrollkästchen **Symbolinformationen automatisch serialisieren**.  
  
- PACKSYMBOLS ist die entsprechende Befehlszeilenoption, wenn Sie Berichtsdateien speichern. Zum Serialisieren von Symbolen geben Sie **vsperfreport /summary:all /packsymbols filename.vsp** ein.  
  
## <a name="troubleshooting-symbol-problems"></a>Problembehandlung bei Symbolen  
 Wenn Sie im eigenen Code keine Symbole sehen, sind einige allgemeine Lösungen verfügbar:  
  
- Führen Sie vsperfreport /debugsympath auf einer Befehlszeile aus, um eine vollständige Liste der Speicherorte, in die Profilerkomponenten Symbolinformationen laden, und Informationen dazu anzuzeigen, ob die verwendeten Symboldateien mit den Dateien übereinstimmen, die Ihr Projekt verwendet.  
  
- Stellen Sie sicher, dass Sie vsperfreport mit dem Flag /PACKSYMBOLS ausführen, bzw. dass Sie im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE die Option für die Serialisierung von Symbolinformationen in den allgemeinen Leistungs-Explorer-Optionen ausgewählt haben.  
  
- Wenn Sie Typdaten erfasst haben, fügen Sie der vsperfreport-Befehlszeile /SUMMARY:TYPE hinzu.  
  
  Wenn Symbole von Windows oder anderen Microsoft-Programmen nicht angezeigt werden:  
  
- Stellen Sie sicher, dass Sie den Pfad des Windows-Symbolcaches festgelegt haben. Führen Sie eine der folgenden Schritte durch, um den Symbolcachepfad festzulegen:  
  
  - Legen Sie die Debugger-> Symbole-Option im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE auf den richtigen Pfad fest.  
  
  - Fügen Sie der VSPerfReport-Befehlszeile die Option -symbolpath hinzu, um Ihre Symbole einzuschließen.  
  
- Wenn keine Symbole in [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] angezeigt werden, stellen Sie sicher, dass Sie den Symbolserver ordnungsgemäß für den ASP-Server eingerichtet haben.  
  
## <a name="repacking-symbols"></a>Erneutes Packen von Symbolen  
 Wenn Sie Symbole erneut in einen Bericht packen möchten, können Sie dazu das Befehlszeilentool VsPerfReport verwenden. Verwenden Sie folgende Befehlszeilen:  
  
 VsPerfReport -clearpackedsymbols filename.vsp  
  
 VsPerfReport -packsymbols -summary:all filename.vsp  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern und Exportieren von Leistungs Tool Daten](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Gewusst wie: verweisen auf Windows-Symbol Informationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

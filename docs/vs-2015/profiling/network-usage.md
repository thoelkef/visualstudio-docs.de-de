---
title: Analysieren der Netzwerkverwendung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548420"
---
# <a name="network-usage"></a>Netzwerkauslastung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Diagnosetool **Netzwerk** von Visual Studio erfasst mithilfe der [Windows.Web.Http-API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx) Daten zu Netzwerkoperationen. Durch Analysieren der Daten können Sie Probleme wie Zugriffs- und Authentifizierungsprobleme, falsche Cacheverwendung und schlechte Anzeige- und Downloadleistung in den Griff bekommen.  
  
 Das Netzwerktool unterstützt nur universelle Windows-Apps. Andere Plattformen werden derzeit nicht unterstützt.  
  
> [!NOTE]
> Eine ausführlichere Beschreibung des Netzwerk Tools finden Sie unter Einführung in das [Netzwerk Tool von Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Sammeln von Netzwerktooldaten  
 Sie sollten das Tool **Netzwerk** mit einem geöffneten Visual Studio-Projekt auf dem Computer mit Visual Studio ausführen.  
  
1. Öffnen Sie das Projekt in Visual Studio.  
  
2. Klicken Sie im Menü auf **Debuggen & gt; leistungsprofiler...**. Wählen Sie **Netzwerk**aus, und klicken Sie dann auf **starten**.  
  
3. Das Netzwerktool beginnt mit dem Erfassen des HTTP-Datenverkehrs Ihrer App.  
  
    Während der Ausführung der App zeigt die Zusammenfassungsansicht im linken Bereich automatisch eine Liste der erfassten HTTP-Vorgänge an. Wählen Sie ein Element in der Zusammenfassungsansicht aus, um weitere Informationen im Detailbereich rechts anzuzeigen.  
  
4. Klicken Sie auf **Beenden**, um die App zu schließen.  
  
   Das Berichtsfenster sollte in etwa wie folgt aussehen:  
  
   ![Fenster „Netzwerk“](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analysieren von Daten  
 Sie können erfassten HTTP-Datenverkehr analysieren, während die App ausgeführt wird oder nachdem sie geschlossen wurde. Wählen Sie dazu einen der in der Zusammenfassungsansicht angezeigten Netzwerkvorgänge aus.  
  
 Die Zusammenfassungsansicht **Netzwerk** zeigt die Daten der einzelnen ausgeführten Netzwerkoperationen Ihrer App an. Wählen Sie eine Spaltenüberschrift aus, um die Liste zu sortieren, oder wählen Sie die Inhaltstypen aus, die in der Filteransicht **Inhaltstyp** angezeigt werden sollen.  
  
 Wählen Sie **Als HAR speichern** aus, um eine JSON-Datei zu erstellen, die von Drittanbietertools wie Fiddler genutzt werden kann.  
  
 Die Detailansicht **Netzwerk** enthält weitere Informationen zu den einzelnen in der Zusammenfassungsansicht angezeigten Netzwerkoperationen.  
  
 ![Detailbereich des Netzwerktools](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|name|Beschreibung|  
|-|-|  
|**Header**|Informationen zu den Anforderungsheadern des Ereignisses.|  
|**Text**|Die Nutzlastdaten von Anforderung und Antwort.|  
|**Parameter**|Die Parameternamen und Werte der Abfragezeichenfolge.|  
|**Cookies**|Cookiedaten von Antwort und Anforderung.|  
|**Zeiten**|Ein Diagramm der Phasen beim Abrufen der ausgewählten Ressourcen.|  
  
 Die **Zusammenfassungsleiste** in der Ansicht „Netzwerk“ zeigt die jeweils angezeigte Anzahl von Netzwerkoperationen, die Menge der übertragenen Daten, die für das Herunterladen der Daten aufgewendete Zeit und die Anzahl von sichtbaren Fehlern (Anforderungen mit Antworten „4xx“ oder „5xx“).  
  
### <a name="analysis-tips"></a>Tipps für die Analyse  
 Dieses Tool hebt bestimmte Bereiche hervor, die bei der Ausführung von netzwerkbezogenen Analysen nützlich sein können:  
  
1. Anforderungen, die vollständig aus dem Cache bedient werden, werden in der Spalte **Empfangen** als **(aus Cache)** angezeigt. Dies kann dabei helfen, herauszufinden, ob der Cache effektiv genutzt und damit Bandbreite für die Benutzer gespart wird, oder ob versehentlich überflüssige Antworten zwischengespeichert und den Endbenutzern Ihrer Anwendung veraltete Daten bereitgestellt werden.  
  
2. Fehlerantworten (4xx oder 5xx) werden mit einem roten Statuscode in der Spalte **Ergebnisse** angezeigt und auch in der Zusammenfassungsleiste hervorgehoben. So lassen sich unter den vielen potenziellen Anforderungen Ihrer Anwendung Fehler ganz einfach erkennen.  
  
3. Die Schaltfläche für eine strukturierte Ausgabe („Schöndruck“, auf der Registerkarte mit dem Haupttext) verbessert die Lesbarkeit des Inhalts und vereinfacht so das Analysieren großer Mengen von JSON-, XML-, HTML-, CSS-, JavaScript- und TypeScript-Antworten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Profil Erstellungs Tools ohne Debugging](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio-Blog: Einführung in den Netzwerk Inspektor von Visual Studio](https://blogs.msdn.com/b/visualstudio/)   
 [Channel 9-Video: vs Diagnostics Tools – New Network Profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)

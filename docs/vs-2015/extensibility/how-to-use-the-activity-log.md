---
title: 'Vorgehensweise: Verwenden des Aktivitätsprotokolls | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4804f07a673abb99d2b0405b397fe53d2e52f589
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212446"
---
# <a name="how-to-use-the-activity-log"></a>Vorgehensweise: Verwenden des Aktivitätsprotokolls
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages können Nachrichten in das Aktivitätsprotokoll zu schreiben. Dieses Feature ist besonders nützlich zum Debuggen von VSPackages im Einzelhandel-Umgebungen.  
  
> [!TIP]
>  Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio behält einen kontinuierlichen Puffer, der die letzten 100 Einträge sowie die ersten zehn Einträge, die allgemeine Konfigurationsinformationen haben.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Zum Schreiben eines Eintrags im Aktivitätsprotokoll  
  
1.  Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode oder in eine andere Methode, mit Ausnahme der VSPackage-Konstruktor:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Dieser Code Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service auf und wandelt ihn um ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Schreibt einen Informationseintrag in das Aktivitätsprotokoll, die unter Verwendung des Kontexts der aktuellen Kultur.  
  
2.  Wenn das VSPackage geladen wird (in der Regel, wenn ein Befehl aufgerufen wird, oder ein Fenster geöffnet ist), wird der Text in das Aktivitätsprotokoll geschrieben.  
  
### <a name="to-examine-the-activity-log"></a>Das Aktivitätsprotokoll untersuchen  
  
1.  Suchen Sie das Aktivitätsprotokoll im Unterordner für Visual Studio-Daten: *% appdata%* \Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2.  Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Texteditor ein. Hier ist ein typischer Eintrag ein:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Da das Aktivitätsprotokoll auf einen Dienst handelt, ist das Aktivitätsprotokoll in der VSPackage-Konstruktor nicht verfügbar.  
  
 Sie sollten das Aktivitätsprotokoll abrufen, unmittelbar vor der in den sie schreiben. Zwischenspeichern Sie und speichern Sie das Aktivitätsprotokoll für die zukünftige Verwendung nicht.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)


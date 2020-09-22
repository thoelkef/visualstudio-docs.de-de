---
title: 'Vorgehensweise: Verwenden des Aktivitäts Protokolls | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841212"
---
# <a name="how-to-use-the-activity-log"></a>Gewusst wie: Verwenden des Aktivitätsprotokolls
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages können Nachrichten in das Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich für das Debuggen von VSPackages in Einzelhandelsumgebungen.  
  
> [!TIP]
> Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio speichert einen parallelen Puffer der letzten 100 Einträge sowie die ersten zehn Einträge, die allgemeine Konfigurationsinformationen aufweisen.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>So schreiben Sie einen Eintrag in das Aktivitätsprotokoll  
  
1. Fügen Sie diesen Code in die- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode oder in eine beliebige andere Methode ein, mit Ausnahme des VSPackage-Konstruktors:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Mit diesem Code wird der <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienst abgerufen und in eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle umgewandelt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> schreibt einen Informations Eintrag mit dem aktuellen Kultur Kontext in das Aktivitätsprotokoll.  
  
2. Wenn das VSPackage geladen wird (in der Regel, wenn ein Befehl aufgerufen oder ein Fenster geöffnet wird), wird der Text in das Aktivitätsprotokoll geschrieben.  
  
### <a name="to-examine-the-activity-log"></a>So überprüfen Sie das Aktivitätsprotokoll  
  
1. Suchen Sie das Aktivitätsprotokoll im Unterordner für die Visual Studio-Daten: *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML.  
  
2. Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Text-Editor. Dies ist ein typischer Eintrag:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Da es sich bei dem Aktivitätsprotokoll um einen Dienst handelt, ist das Aktivitätsprotokoll im VSPackage-Konstruktor nicht verfügbar.  
  
 Sie sollten das Aktivitätsprotokoll direkt vor dem Schreiben in das Aktivitätsprotokoll abrufen. Speichern oder speichern Sie das Aktivitätsprotokoll nicht für die zukünftige Verwendung.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)

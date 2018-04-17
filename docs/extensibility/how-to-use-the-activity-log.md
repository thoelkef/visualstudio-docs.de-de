---
title: 'Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-activity-log"></a>Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll
VSPackages können Meldungen im Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich zum Debuggen von VSPackages im Einzelhandel Umgebungen.  
  
> [!TIP]
>  Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio speichert einen parallelen Puffer die letzten 100 Einträge sowie die ersten 10 Einträge, die allgemeine Konfigurationsinformationen verfügen.  
  
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
  
     Dieser Code Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service und wandelt es zu einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Schreibt einen Eintrag zu Informationszwecken, in das Aktivitätsprotokoll mit den aktuellen kulturellen Kontext.  
  
2.  Wenn das VSPackage geladen wird (in der Regel, wenn ein Befehl aufgerufen wird, oder ein Fenster geöffnet ist), wird der Text in das Aktivitätsprotokoll geschrieben.  
  
### <a name="to-examine-the-activity-log"></a>Untersuchen Sie das Aktivitätsprotokoll  
  
1.  Führen Sie Visual Studio mit der [/Log](../ide/reference/log-devenv-exe.md) Befehlszeilenschalter ActivityLog.xml während der Sitzung auf dem Datenträger speichert.

2.  Nach dem Schließen von Visual Studio, suchen Sie das Aktivitätsprotokoll im Unterordner "" für Visual Studio-Daten: *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.xml.  
  
3.  Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Texteditor. Hier ist ein typische Eintrag:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Da das Aktivitätsprotokoll auf einen Dienst handelt, steht das Aktivitätsprotokoll im VSPackage-Konstruktor.  
  
 Sie sollten das Aktivitätsprotokoll nur vor dem Schreiben in diese anfordern. Zwischenspeichern Sie und speichern Sie das Aktivitätsprotokoll für die zukünftige Verwendung nicht.  
  
## <a name="see-also"></a>Siehe auch
 [/ Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)

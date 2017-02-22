---
title: "Gewusst wie: Verwenden Sie das Aktivit&#228;tsprotokoll | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen von VSPackages"
  - "VSPackages, Problembehandlung"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Verwenden Sie das Aktivit&#228;tsprotokoll
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages können Nachrichten in Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich zum Debuggen von VSPackages im Einzelhandel.  
  
> [!TIP]
>  Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio behält einen kontinuierlichen Puffer die letzten 100 Einträge sowie die ersten zehn Einträge, die allgemeine Konfigurationsinformationen verfügen.  
  
### Um einen Eintrag im Aktivitätsprotokoll schreiben  
  
1.  Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode oder in eine andere Methode, mit Ausnahme der VSPackage\-Konstruktor:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Dieser Code Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service und wandelt es zu einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle.<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Schreibt einen informativen Eintrag in das Aktivitätsprotokoll mit den aktuellen kulturellen Kontext.  
  
2.  Wenn das VSPackage geladen wird \(in der Regel, wenn ein Befehl aufgerufen wird, oder ein Fenster geöffnet ist\), wird der Text im Aktivitätsprotokoll geschrieben.  
  
### Überprüfen Sie das Aktivitätsprotokoll  
  
1.  Suchen Sie das Aktivitätsprotokoll im Unterordner für Visual Studio\-Daten: *% appdata%*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  Öffnen Sie das Aktivitätsprotokoll mit einem Text\-Editor. Hier ist ein typischer Eintrag:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## Robuste Programmierung  
 Da das Aktivitätsprotokoll auf einen Dienst handelt, ist das Aktivitätsprotokoll VSPackage Konstruktor nicht verfügbar.  
  
 Bevor Sie darauf schreiben, sollte das Aktivitätsprotokoll abgerufen werden. Zwischenspeichern Sie und speichern Sie das Aktivitätsprotokoll für die zukünftige Verwendung nicht.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
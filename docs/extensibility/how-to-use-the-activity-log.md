---
title: "Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: dc821f22a04432989a2edb68c483d298ffcf0eb7
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-the-activity-log"></a>Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll
VSPackages können Meldungen im Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich zum Debuggen von VSPackages im Einzelhandel Umgebungen.  
  
> [!TIP]
>  Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio speichert einen parallelen Puffer die letzten 100 Einträge sowie die ersten zehn Einträge, die allgemeine Konfigurationsinformationen verfügen.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Zum Schreiben eines Eintrags im Aktivitätsprotokoll  
  
1.  Fügen Sie diesen Code in der Methode < xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A > oder in eine andere Methode, mit Ausnahme der VSPackage-Konstruktor:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Dieser Code wird der Dienst < xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog > abgerufen und in einer Schnittstelle < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog > umgewandelt. < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A > schreibt einen Eintrag das Aktivitätsprotokoll mit den aktuellen kulturellen Kontext nur zu Informationszwecken.  
  
2.  Wenn das VSPackage geladen wird (in der Regel, wenn ein Befehl aufgerufen wird, oder ein Fenster geöffnet ist), wird der Text in das Aktivitätsprotokoll geschrieben.  
  
### <a name="to-examine-the-activity-log"></a>Untersuchen Sie das Aktivitätsprotokoll  
  
1.  Suchen Sie das Aktivitätsprotokoll im Unterordner "" für Visual Studio-Daten: *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Texteditor. Hier ist ein typische Eintrag:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Da das Aktivitätsprotokoll auf einen Dienst handelt, steht das Aktivitätsprotokoll im VSPackage-Konstruktor.  
  
 Sie sollten das Aktivitätsprotokoll nur vor dem Schreiben in diese anfordern. Zwischenspeichern Sie und speichern Sie das Aktivitätsprotokoll für die zukünftige Verwendung nicht.  
  
## <a name="see-also"></a>Siehe auch  
 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >   
 < xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE >   
 [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)


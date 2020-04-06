---
title: 'Gewusst wie: Verwenden des Aktivitätsprotokolls | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710583"
---
# <a name="how-to-use-the-activity-log"></a>Gewusst wie: Verwenden des Aktivitätsprotokolls
VSPackages kann Nachrichten in das Aktivitätsprotokoll schreiben. Diese Funktion ist besonders nützlich für das Debuggen von VSPackages in Einzelhandelsumgebungen.

> [!TIP]
> Das Aktivitätsprotokoll ist immer aktiviert. Visual Studio speichert einen rollierenden Puffer der letzten 100 Einträge sowie der ersten 10 Einträge, die allgemeine Konfigurationsinformationen enthalten.

## <a name="to-write-an-entry-to-the-activity-log"></a>So schreiben Sie einen Eintrag in das Aktivitätsprotokoll

1. Fügen Sie diesen <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Code in die Methode oder in eine andere Methode mit Ausnahme des VSPackage-Konstruktors ein:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Dieser Code <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> ruft den Dienst ab <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> und gibt ihn in eine Schnittstelle um. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>schreibt einen Informationseintrag in das Aktivitätsprotokoll unter Verwendung des aktuellen kulturellen Kontexts.

2. Wenn das VSPackage geladen wird (normalerweise, wenn ein Befehl aufgerufen oder ein Fenster geöffnet wird), wird der Text in das Aktivitätsprotokoll geschrieben.

## <a name="to-examine-the-activity-log"></a>So untersuchen Sie das Aktivitätsprotokoll

1. Führen Sie Visual Studio mit dem Befehlszeilenschalter [/Log](../ide/reference/log-devenv-exe.md) aus, um ActivityLog.xml während der Sitzung auf den Datenträger zu schreiben.

2. Suchen Sie nach dem Schließen von Visual Studio das Aktivitätsprotokoll im Unterordner für Visual Studio-Daten:

   <em> *%AppData%</em>, Microsoft-VisualStudio-Version\\\<>.*

3. Öffnen Sie das Aktivitätsprotokoll mit einem beliebigen Texteditor. Hier ist ein typischer Eintrag:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Stabile Programmierung

Da es sich bei dem Aktivitätsprotokoll um einen Dienst handelt, ist das Aktivitätsprotokoll im VSPackage-Konstruktor nicht verfügbar.

Sie sollten das Aktivitätsprotokoll kurz vor dem Schreiben abrufen. Cachen oder Speichern Sie das Aktivitätsprotokoll nicht für die zukünftige Verwendung.

## <a name="see-also"></a>Weitere Informationen

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)

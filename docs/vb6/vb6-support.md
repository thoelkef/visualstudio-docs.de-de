---
title: Unterstützt Sie bei Visual Basic 6.0-Anweisung | Microsoft Docs
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload:
- paulyuk
ms.openlocfilehash: cc55dec5960717e3807602bc76031f7502ec90c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Supportinformationen Sie für Visual Basic 6.0 unter Windows


## <a name="executive-summary"></a>Kurzfassung

Visual Basic-Team zugesichert ist "It Just Works" Kompatibilität mit Visual Basic 6.0-Anwendungen auf der folgenden unterstützten Windows-Betriebssysteme: 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 R2 einschließlich
- Windows Server 2008 R2 einschließlich

Das Visual Basic-Team-Ziel ist es, dass Visual Basic 6.0-Anwendungen weiter Daten auf unterstützten Windows-Versionen ausgeführt werden. Wie in diesem Dokument ausführlich, wird die Visual Basic 6.0-Core-Laufzeit für die gesamte Lebensdauer der unterstützten Windows-Versionen, die fünf Jahre grundlegender Support gefolgt von fünf Jahren des erweiterten Support ist unterstützt werden (http://support.microsoft.com/gp/lifepolicy). Die Support-Leiste sind wichtige Sicherheitsprobleme für vorhandene Anwendungen zu schweren Regressionen beschränkt.

## <a name="technical-summary"></a>Technische Übersicht

Visual Basic 6.0 diese Schlüsselergebnisse besteht:
- Visual Basic 6.0-IDE (Integrated Development Environment).
- Visual Basic 6.0-Runtime: die Basis-Bibliotheken und das Ausführungsmodul zum Ausführen von Visual Basic 6.0-Anwendungen verwendet.
- Visual Basic 6.0 Extended-Runtimedateien: ausgewählten ActiveX-Steuerelement OCX-Dateien, Bibliotheken und Tools, die den Protokollversand mit den IDE-Medien und als ein online-Version.

## <a name="the-visual-basic-60-ide"></a>Der Visual Basic 6.0-IDE

Der Visual Basic 6.0-IDE ab 8. April 2008 nicht mehr unterstützt. Darüber hinaus wurden die Windows- und Visual Basic-Teams IDE von Visual Basic 6.0 auf Windows Vista, Windows 7, Windows Server 2008, Windows 8 und Windows 8.1 zu verstehen und zu mindern, (falls zutreffend) getestet Kompatibilitätsprobleme auf 32-Bit-Versionen von Windows (Siehe die [64-Bit-Windows](#62-bit-windows) weiter unten im Abschnitt Weitere Informationen zur 64-Bit-Systeme). Diese Ankündigung ändert nicht die Supportrichtlinie für die IDE.

## <a name="the-visual-basic-60-runtime"></a>Die Visual Basic 6.0-Laufzeit

Die Visual Basic 6.0-Laufzeit ist definiert als die kompilierten Binärdateien, die ursprünglich in der Neuverteilungsliste für Visual Basic 6.0 enthalten. Diese Dateien wurden als in der ursprünglichen Visual Basic 6.0-Lizenz verteilbarer gekennzeichnet. Beispiele für diese Dateien sind die Visual Basic 6.0-Laufzeitbibliothek (`msvbvm60.dll`), Steuerelemente (d. h. `msflxgrd.ocx`) zusammen mit der Common Language Runtime-Unterstützungsdateien für andere Hauptfunktionsbereiche (d. h. MDAC).

Die Common Language Runtime ist in drei Gruppen unterteilt:

- Unterstützt die Common Language runtimedateien auf dem Betriebssystem Protokollversand

   In den meisten Anwendungsszenarios verwendete Schlüssel Visual Basic 6.0-runtimedateien geliefert werden und für die Lebensdauer der unterstützten Windows-Versionen unterstützt. Diese Lebensdauer ist fünf Jahre grundlegender Support und fünf Jahre des erweiterten Support von der Zeit, die eine bestimmte Version von Windows bereitgestellt wird. Diese Dateien wurden als Teil unserer Tests von Visual Basic 6.0-Anwendungen unter unterstützten Windows-Versionen aus Kompatibilitätsgründen getestet. 

   > [!NOTE]
   > Alle unterstützten Windows-Versionen enthalten eine fast identische Liste der Dateien und die Redist-Anforderungen für Anwendungen, die mit diesen Dateien fast identisch sein. Ein Hauptunterschied besteht darin, die `TriEdit.dll` wurde von Windows Vista und höheren Versionen entfernt.

- Unterstützt die Common Language runtimedateien –-Dateien mit der Anwendung verteilen von erweiterten

   Diese erweiterte Liste besteht aus-Steuerelemente, Bibliotheken und Tools, die über die IDE-Medium oder "Microsoft.com" mit dem Entwicklercomputer installiert sind. In der Regel installiert der IDE VB6 diese Steuerelemente an den Entwicklercomputer standardmäßig. Der Entwickler muss weiterhin auf diese Dateien mit der Anwendung verteilen. Die unterstützte Version der Dateien steht online im Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- Nicht unterstützte runtimedateien

   Einige Dateien entweder außerhalb des gültigen grundlegender nachrichtenumfang unterstützen oder wurden nicht als Teil der Common Language Runtime Redist enthalten (z. B. wurden sie in enthalten die `\Tools` Ordner auf dem IDE-Medium zur Unterstützung von VB4/VB5 Legacyanwendungen oder Steuerelemente von Drittanbietern waren). Diese Dateien werden unter Windows nicht unterstützt. Stattdessen unterliegen sie beliebige Supportvertrag für das Medium gilt, die sie mit geliefert wurden. Dies bedeutet ohne Garantien zur Verfügung, um Support und Wartung. In einigen Fällen werden dieser Bibliotheken höhere Versionen unterstützt. Informationen zur Abwärtskompatibilität oder Migration zu unterstützten Versionen sind weiter unten.

Weitere Details dazu, die in jede Supportgruppe enthaltenen Dateien finden Sie unter der [Runtime Definition](#runtime-definition) Abschnitt weiter unten.

## <a name="the-visual-basic-60-support-lifetime"></a>Die Lebensdauer der Visual Basic 6.0-Unterstützung

Unterstützende und/oder Protokollversand von Visual Basic 6.0-Laufzeit-Binärdateien auf unterstützten Windows-Versionen wird nicht die Supportrichtlinie für die IDE von Visual Basic 6.0 oder Visual Studio-IDE 6.0 als Ganzes geändert. Die Produkte, die aus dem erweiterten Support am 8. April 2008 verschoben werden.

Informationen zum Support Lifecycle von Microsoft-Produkten finden Sie unter http://support.microsoft.com/gp/lifepolicy. Microsoft weiterhin als Teil dieses Lebenszyklus unterstützen die Visual Basic 6.0-Laufzeit unter unterstützten Windows-Versionen für die Lebensdauer der Unterstützung dieser Betriebssysteme unterstützen. Dies bedeutet beispielsweise, dass die Visual Basic 6.0-Laufzeit unter Windows Server 2003 bis Juni 2008 für Mainstream-Support und Juni 2013 für erweiterte Unterstützung für die unterstützt werden.
Weitere Informationen zum Support Lifecycle oder Informationen zu weiteren Supportoptionen erhalten finden Sie auf unserer Support-Website http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>64-Bit-Windows

Visual Basic 6.0-runtimedateien sind 32-Bit. Diese Dateien ausgeliefert in 64-Bit-Windows-Betriebssystemen auf, die in der folgenden Tabelle verwiesen wird. 32-Bit-VB6 Anwendungen und-Komponenten werden in nur der WOW-emulationsumgebung unterstützt. 32-Bit-Komponenten müssen auch in 32-Bit-Anwendungsprozessen gehostet werden.

Der Visual Basic 6.0-IDE wurde nie in einer systemeigenen 64-Bit-Version bereitgestellt wurde, noch ist die 32-Bit-IDE auf 64-Bit-Windows unterstützt. VB6-Entwicklung unter Windows 64-Bit-oder eine beliebige systemeigene Architektur als 32-Bit-nicht und wird nicht unterstützt.

## <a name="windows-7"></a>Windows 7

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde das Betriebssystem Windows 7 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows 7 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows 7 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden.

## <a name="windows-81"></a>Windows 8.1

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde das Betriebssystem Windows 8.1 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 auf Windows 8.1 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows 8.1 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows 8.1 wird die gleiche wie für Windows 7.

## <a name="windows-10"></a>Windows 10

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde das Betriebssystem Windows 10 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows 10 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows 10 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows 10 wird die gleiche wie für Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde das Betriebssystem Windows Server 2008 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows Server 2008 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows Server 2008 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde des Betriebssystems Windows Server 2008 R2 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows Server 2008 R2 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows Server 2008 R2 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows Server 2008 R2 wird die gleiche wie für Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde des Betriebssystems Windows Server 2012 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows Server 2012 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows Server 2012 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows Server 2012 wird die gleiche wie für Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde des Betriebssystems Windows Server 2012 R2 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows Server 2012 R2 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows Server 2012 R2 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows Server 2012 R2 wird die gleiche wie für Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

Seit der Erstveröffentlichung von diese Aussage zur Unterstützung wurde des Betriebssystems Windows Server 2016 freigegeben. Dieses Dokument wurde aktualisiert, um Microsoft Support für VB6 unter Windows Server 2016 zu verdeutlichen.

Die Laufzeit VB6 ausgeliefert und wird für die Lebensdauer des Betriebssystems in Windows Server 2016 unterstützt. Visual Basic 6.0-runtimedateien weiterhin nur 32-Bit-sein und müssen alle Komponenten in Prozessen 32-Bit-Anwendung gehostet werden. Entwickler können sichereres Story Unterstützung für Windows Server 2016 wird die gleiche wie für Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Unterstützte Windows-Betriebssystemversionen

Dieser Abschnitt enthält zusätzliche Informationen zu den Betriebssystemen, die einige Maß an Unterstützung für VB6 bieten. 

|Windows-Betriebssystem|VB6 Unterstützt die Common Language Runtime</br>Dateien, die in Windows den Protokollversand bieten Unterstützung?|VB6 Unterstützte Rutime</br>Dateien von erweiterten</br>mit der Anwendung verteilen unterstützen?| VB6 IDE verfügt über Unterstützung?|
|---|---|---|---|
|Windows 10, alle 32-Bit-Editionen|Ja *|Ja *|Nein|
|Windows 10, alle 64-Bit-Editionen (nur WOW)|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows 8.1, alle 32-Bit-Editionen|Ja *|Ja *|Nein|
| Windows 8.1, alle 64-Bit-Editionen (nur WOW)|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows 7, alle 32-Bit-Editionen|Ja *|Ja *|Nein|
|Windows 7, alle 64-Bit-Editionen (nur WOW)|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows Server 2016, alle 64-Bit-Editionen (nur WOW)|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows Server 2012 R2, alle 64-Bit-Editionen (nur WOW)<br>Windows Server 2012, alle 64-Bit-Editionen (nur WOW)|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja* </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows Server 2008 R2, alle X64 Editionen (nur WOW)</br>Windows Server 2008, alle X64 Editionen (nur WOW)|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Ja * </br> 32-Bit-apps, die nur im WOW-Modus ausgeführt wird|Nein|
|Windows Server 2008, alle 32-Bit-Editionen|Ja *|Ja *|Nein|


> [!NOTE]
> &#42;VB6-Runtime-Unterstützung wird durch den Lebenszyklus der Windows-Unterstützung beschränkt.  Beispielsweise ist Zielbetriebssystem unter den erweiterten Support VB6 ein höheres Maß an Unterstützung als erweiterten Support nicht möglich.  Die [Windows support Lifecycle-Merkblatt](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) enthält zusätzliche Lifecycle Informationen über vorherige und aktuelle Windows-Versionen.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Visual Basic 6.0 Common Language Runtime Verwendung innerhalb von VBA- und Office

Visual Basic for Applications oder VBA, ist eine unterschiedliche Technologie, die häufig für Anwendung Automatisierung und Makros in anderen Anwendungen, die am häufigsten in Microsoft Office-Anwendungen verwendet. VBA wird als Teil von Office bereitgestellt und aus diesem Grund wird die Unterstützung für VBA gesteuert, die Richtlinie für die Unterstützung von Office. Es gibt jedoch Situationen, in denen VBA aufrufen oder Visual Basic 6.0-Runtime-binarys und Steuerelemente des Hosts verwendet wird. In diesen Fällen Visual Basic 6.0 Common Language runtimedateien in das Betriebssystem unterstützt, und die Dateiliste für den erweiterten werden ebenfalls unterstützt, wenn in einer unterstützten VBA-Umgebung verwendet.

Für VB6 Laufzeitszenarien innerhalb von VBA unterstützt werden müssen müssen alle folgenden erfüllt sein:

- Der Host-Betriebssystemversion für VB-Laufzeit wird weiterhin unterstützt.
- Die Hostversion von Office VBA wird weiterhin unterstützt.
- Die Common Language runtimedateien, die fragliche werden weiterhin unterstützt.

## <a name="visual-basic-script-vbscript"></a>Visual Basic-Skript (VBScript)

VBScript ist unabhängig von Visual Basic 6.0 und diese Aussage zur Unterstützung. Allerdings VBScript ist derzeit als Teil von Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012 R2 und Windows Server 2016 einschließlich einschließlich Versand und OS Support Lifecycle unterliegt.

## <a name="third-party-components"></a>Drittanbieter-Komponenten

Microsoft kann nicht auf Komponenten von Drittanbietern, z. B. OCX/ActiveX-Steuerelemente unterstützen. Kunden werden empfohlen, wenden Sie sich an den Hersteller des ursprünglichen Steuerelements für Informationen zur Unterstützung für diese Komponenten.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Melden von Problemen mit Visual Basic 6.0-Anwendungen unter Windows

Planen der Verwendung von Visual Basic 6.0 mit einem der aufgelisteten Windows-Betriebssysteme Entwickler dieses Betriebssystem installieren und Anwendungskompatibilitätstests mithilfe der ursprünglichen Anwendung Akzeptanztests beginnen.

Wenn Sie ein Problem mit der Visual Basic 6.0-Anwendung, die Ausführung auf einem der aufgelisteten Windows-Betriebssysteme gefunden haben, befolgen Sie die normalen Supportkanäle, um das Problem zu melden.

## <a name="supported-and-shipping-in-windows"></a>Unterstützte und Versandkosten in Windows

| | | | |
|---|---|---|---|
|ATL.dll|         msadcor.dll|     msorcl32.dll|   OLE2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   Ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|Dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|ds16gt.dll|      msadrh15.dll|    odbc16gt.dll|   "OLEPRO32.dll"|
|ds32gt.dll|      mscpxl32.dll|    odbc32.dll|     olethk32.dll|
|Expsrv.dll|      msdadc.dll|      odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|Hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   "rpcrt4.dll"|
|imagehlp.dll|    msdaora.dll|     odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   Secur32.dll|
|itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|Itss.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   Sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Unterstützte runtimedateien mit der Anwendung verteilen.

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |"Msflxgrd.ocx"  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|Comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |Picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |"Richtx32.ocx"| 
|dblist32.ocx |MSDATGRD.ocx |msmask32.ocx  |sysinfo.ocx|  
|Mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Nicht unterstützt, jedoch kompatibel und unterstützt Updates bzw. Upgrades verfügbar sind.

| | | | |
|---|---|---|---|
|Dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Nicht unterstützte runtimedateien

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  VisData.exe|
|AUTMGR32.exe| ciscnfg.exe|  RPCSS.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|RACMGR32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  Windbver.exe|  Tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Lokalisierung Unterstützung Binärdateien

Die folgenden Binärdateien sind erforderlich, für die Unterstützung von Visual Basic 6.0-Anwendungen, die auf lokalisierte Versionen von Windows-Betriebssystem ausgeführt wird. Sie werden unterstützt, jedoch sind nicht im Lieferumfang von Windows. Diese Dateien sind erforderlich, um mit Setup Ihrer Anwendung ausgeliefert werden.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Unterstützte runtimedateien mit der Anwendung verteilen.

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     VB6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|


---
title: Analysieren von Tests der programmierten Benutzeroberfläche mithilfe der Testprotokolle der programmierten Benutzeroberfläche | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3ebb18aaff78d9782b6210e25bcd697d21c8570
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660764"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testprotokolle für codierte UI filtern wichtige Informationen zum ausgeführten Test der codierten UI und zeichnen diese auf.

 **Anforderungen**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Warum sollte ich das tun?
 Die Protokolle werden in einem Format dargestellt, mit dem sich Probleme schnell debuggen lassen.

## <a name="how-do-i-do-this"></a>Wie geht das?

### <a name="step-1-enable-logging"></a>Schritt 1: Aktivieren der Protokollierung
 Verwenden Sie je nach Szenario eine der folgenden Methoden zur Aktivierung des Protokolls.

- Auf .NET Framework Version 4 abzielen, wenn keine Datei App.config im Testprojekt vorhanden ist

  - Öffnen Sie die Datei **QTAgent32_40.exe.config**.

    Standardmäßig befindet sich diese Datei unter " ** \<drvie> : \Programme (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**".

    Ändern Sie den Wert für EqtTraceLevel auf die gewünschte Protokollebene.

    Speichern Sie die Datei.

- Auf .NET Framework Version 4,5 abzielen, wenn keine Datei App.config im Testprojekt vorhanden ist

  - Öffnen Sie die Datei **QTAgent32.exe.config**.

    Standardmäßig befindet sich diese Datei unter " ** \<drvie> : \Programme (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**".

    Ändern Sie den Wert für EqtTraceLevel auf die gewünschte Protokollebene.

    Speichern Sie die Datei.

- Datei App.config im Testprojekt vorhanden

  - Öffnen Sie die Datei App.config im Projekt.

    Fügen Sie unter dem Konfigurationsknoten den folgenden Code hinzu:

    `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`

- Die Anmeldung aus dem Testcode selbst aktivieren

  - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Schritt 2: Den Test der programmierten UI ausführen und das Protokoll anzeigen
 Wenn Sie einen Test der programmierten Benutzeroberfläche mit der modifizierten Datei **QTAgent32.exe.config** ausführen, dann sehen Sie, dass es einen Ausgabelink in den Ergebnissen des Test-Explorers gibt. Protokolldateien werden nicht nur produziert, wenn der Test fehlschlägt, sondern auch für erfolgreiche Tests, wenn das Level der Ablaufverfolgung auf "verbose" gesetzt ist.

1. Wählen Sie im Menü **Test** die Option **Fenster** aus, und wählen Sie dann **Test-Explorer**aus.

2. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

3. Wählen Sie im Test-Explorer den Test der programmierten UI aus, den Sie ausführen möchten, öffnen Sie das Kontextmenü, und wählen Sie dann **Tests ausführen**aus.

     Die automatisierten Tests werden ausgeführt und geben an, wenn sie erfolgreich waren oder Fehler aufgetreten sind.

    > [!TIP]
    > Um Test-Explorer über das **Testmenü** anzuzeigen, zeigen Sie auf **Fenster**, und wählen Sie **Test-Explorer** aus.

4. Wählen Sie den Link **Ausgabe** in den Ergebnissen des Test-Explorers aus.

     ![Ausgabelink im Test-Explorer](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")

     Damit wird die Ausgabe für den Test angezeigt, in der ein Link zum Aktionsprotokoll enthalten ist.

     ![Ergebnisse und Ausgabelinks aus Test der codierten UI](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")

5. Wählen Sie den Link UITestActionLog.html.

     Das Protokoll wird im Webbrowser angezeigt.

     ![Protokolldatei aus Test der codierten UI](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")

## <a name="q--a"></a>Fragen und Antworten

### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>F: Was ist mit dem Schlüssel EnableHtmlLogger passiert?
 In früheren Versionen von Visual Studio gab es zwei zusätzliche Konfigurationseinstellungen mit denen der HtmlLogger in Coded UI-Test aktiviert werden konnte:

```

<add key="EnableHtmlLogger" value="true"/>

<add key="EnableSnapshotInfo" value="true"/>

```

 Diese beiden Einstellungen sind ab Visual Studio 2012 veraltet. Sie müssen nur noch die Einstellung EqtTraceLevel ändern, damit HtmlLogger aktiviert wird.

## <a name="see-also"></a>Weitere Informationen
 [Verwenden Sie die Benutzeroberflächen Automatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md) Gewusst [wie: Ausführen von Tests aus Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

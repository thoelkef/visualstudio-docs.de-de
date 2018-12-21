---
title: Erstellen eines Aufzeichnungs-Plug-Ins für Webleistungstests
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 822c5cc1b657e6b5ada886ef7f10219a42df723a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064626"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Vorgehensweise: Erstellen eines Aufzeichnungs-Plug-Ins

Das <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> ermöglicht das Ändern eines aufgezeichneten Webleistungstests. Die Änderung wird vorgenommen, nachdem Sie in der Symbolleiste der **Webleistungstest-Aufzeichnung** auf **Beenden** klicken, jedoch vor dem Speichern und Anzeigen des Tests im Webleistungstest-Editor.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ein Aufzeichnungs-Plug-In ermöglicht Ihnen, Ihre eigene benutzerdefinierte Korrelation auf dynamische Parameter auszuführen. Durch die integrierte Korrelationsfunktion erkennen Webleistungstests die dynamischen Parameter in der Webaufzeichnung nach ihrer Ausführung oder bei Auswahl der Option **Dynamische Parameter auf Webtestparameter hochstufen** in der Symbolleiste des **Webleistungstest-Editors**. Die integrierte Erkennungsfunktion findet jedoch nicht immer alle dynamischen Parameter. Eine Sitzungs-ID, deren Wert normalerweise innerhalb von 5 bis 30 Minuten geändert wird, wird z. B. nicht gefunden. Daher müssen Sie den Korrelationsprozess manuell ausführen.

Das <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> ermöglicht das Schreiben von Code für ein eigenes benutzerdefiniertes Plug-In. Dieses Plug-In kann eine Korrelation ausführen oder den Webleistungstest in unterschiedlicher Weise ändern, bevor er gespeichert und im Webleistungstest-Editor angezeigt wird. Wenn Sie feststellen, dass eine bestimmte dynamische Variable für viele Aufzeichnungen korreliert werden muss, können Sie den Prozess daher automatisieren.

Ein Aufzeichnungs-Plug-In kann in einem Webleistungstest auch zum Hinzufügen von Extraktions- und Validierungsregeln, Hinzufügen von Kontextparametern oder Konvertieren von Kommentaren in Transaktionen verwendet werden.

In den folgenden Prozeduren wird beschrieben, wie Sie den rudimentären Code für ein Aufzeichnungs-Plug-In erstellen und das Plug-In bereitstellen und ausführen. Im Beispielcode im Anschluss an die Prozeduren wird veranschaulicht, wie ein benutzerdefiniertes Aufzeichnungs-Plug-In für die Korrelation dynamischer Parameter mit Visual C# erstellt wird.

## <a name="create-a-recorder-plug-in"></a>Erstellen eines Aufzeichnungs-Plug-Ins

### <a name="to-create-a-recorder-plug-in"></a>So erstellen Sie ein Aufzeichnungs-Plug-In

1.  Öffnen Sie eine Projektmappe, die das Webleistungs- und Auslastungstestprojekt mit dem Webleistungstest enthält, für den Sie ein Aufzeichnungs-Plug-In erstellen möchten.

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, wählen Sie **Hinzufügen** aus, und klicken Sie anschließend auf **Neues Projekt**.

     Das Dialogfeld **Neues Projekt hinzufügen** wird angezeigt.

3.  Wählen Sie unter **Installierte Vorlagen** den Eintrag **Visual C#** aus.

4.  Wählen Sie in der Liste der Vorlagen **Klassenbibliothek** aus.

5.  Geben Sie im Textfeld **Name** einen Namen für das Aufzeichnungs-Plug-In ein.

     Die Klassenbibliothek wird zum **Projektmappen-Explorer** hinzugefügt, und die neue Klasse wird im **Code-Editor** geöffnet.

6.  Klicken Sie im **Projektmappen-Explorer** im Ordner des neuen Klassenbibliotheksprojekts mit der rechten Maustaste auf den Ordner **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

    > [!TIP]
    > Ein Beispiel für den Ordner eines neuen Klassenbibliothekprojekts ist **RecorderPlugins**.

     Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

7.  Wählen Sie die Registerkarte **.NET** aus.

8.  Scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** aus und klicken dann auf **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** wird im **Projektmappen-Explorer** zum Ordner **Verweise** hinzugefügt.

9. Schreiben Sie den Code für das Aufzeichnungs-Plug-In. Erstellen Sie zunächst eine neue öffentliche Klasse, die von <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> abgeleitet wird.

10. Überschreiben Sie die <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> -Methode.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Die Ereignisargumente liefern zwei Objekte, mit denen Sie arbeiten können: das aufgezeichnete Ergebnis und den aufgezeichneten Webleistungstest. So können Sie das Ergebnis durchlaufen und nach bestimmten Werten suchen und anschließend im Webleistungstest zur gleichen Anforderung springen, um Änderungen vorzunehmen. Sie können auch nur den Webleistungstest ändern, wenn Sie einen Kontextparameter hinzufügen oder Teile der URL parametrisieren möchten.

    > [!NOTE]
    > Wenn Sie den Webleistungstest ändern, müssen Sie auch die <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*>-Eigenschaft auf „TRUE“ festlegen: `e.RecordedWebTestModified = true;`

11. Fügen Sie entsprechend den Aktionen, die das Aufzeichnungs-Plug-In nach der Webaufzeichnung ausführen soll, weiteren Code hinzu. Sie können z. B. Code hinzufügen, um die benutzerdefinierte Korrelation wie im folgenden Beispiel dargestellt zu behandeln. Ein Aufzeichnungs-Plug-In kann auch für Aufgaben wie das Konvertieren von Kommentaren in Transaktionen oder Hinzufügen von Validierungsregeln zum Webleistungstest erstellt werden.

12. Klicken Sie im Menü **Erstellen** auf **\<Name des Klassenbibliotheksprojekts> erstellen**.

13. Als Nächstes müssen Sie das Aufzeichnungs-Plug-In bereitstellen, um es in Visual Studio zu registrieren.

### <a name="deploy-the-recorder-plug-in"></a>Bereitstellen des Aufzeichnungs-Plug-Ins

Nachdem Sie das Aufzeichnungs-Plug-In kompiliert haben, speichern Sie die sich ergebende DLL-Datei an einem von zwei Speicherorten:

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[version]\\[edition]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [version]\WebTestPlugins*

> [!WARNING]
> Nachdem Sie das Aufzeichnungs-Plug-In an einen dieser Speicherorte kopiert haben, müssen Sie Visual Studio neu starten, damit das Aufzeichnungs-Plug-In registriert wird.

### <a name="to-execute-the-recorder-plug-in"></a>So führen Sie das Aufzeichnungs-Plug-In aus

1.  Erstellen Sie einen neuen Webleistungstest.

     Das Dialogfeld **WebTestRecordPlugins aktivieren** wird angezeigt.

2.  Aktivieren Sie das Kontrollkästchen für das Aufzeichnungs-Plug-In, und klicken Sie auf **OK**.

     Nachdem der Webleistungstest die Aufzeichnung abgeschlossen hat, wird das neue Aufzeichnungs-Plug-In ausgeführt.

    > [!WARNING]
    > Möglicherweise erhalten Sie eine Fehlermeldung wie die folgende, wenn Sie einen Webleistungstest oder einen Auslastungstest ausführen, der das Plug-In verwendet:
    >
    > **Fehler bei der Anforderung: Ausnahme in \<plug-in>-Ereignis: Die Datei oder Assembly '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' oder eine ihrer Abhängigkeiten konnte nicht geladen werden. Das System konnte die angegebene Datei nicht finden.**
    >
    > Ein solcher Fehler wird verursacht, wenn Sie an einem der Plug-Ins Codeänderungen vornehmen und eine neue DLL-Version **(Version=0.0.0.0)** erstellen, während das Plug-In weiterhin auf die ursprüngliche Plug-In-Version verweist. Um dieses Problem zu beheben, führen Sie folgende Schritte aus:
    >
    > 1. Im Webleistungs- und Auslastungstestprojekt wird in Verweisen eine Warnung angezeigt. Entfernen Sie den Verweis auf die Plug-In-DLL, und fügen Sie ihn wieder hinzu.
    > 2. Entfernen Sie das Plug-In aus dem Test oder vom entsprechenden Speicherort, und fügen Sie es dann wieder hinzu.

## <a name="example"></a>Beispiel

In diesem Beispiel wird veranschaulicht, wie ein benutzerdefiniertes Aufzeichnungs-Plug-In für Webleistungstests erstellt wird, um eine benutzerdefinierte Korrelation dynamischer Parameter auszuführen.

> [!NOTE]
> Eine vollständige Auflistung des Beispielcodes finden Sie am Ende dieses Themas.

**Überprüfen des Beispielcodes**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Durchlaufen des Ergebnisses, um nach der ersten Seite mit "ReportSession" zu suchen

In diesem Teil des Codebeispiels wird jedes aufgezeichnete Objekt durchlaufen und im Antworttext nach "ReportSession" gesucht.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

## <a name="add-an-extraction-rule"></a>Hinzufügen einer Extraktionsregel

Nachdem eine Antwort gefunden wurde, müssen Sie eine Extraktionsregel hinzufügen. In diesem Teil des Codebeispiels wird die Extraktionsregel mithilfe der <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>-Klasse erstellt, und anschließend wird im Webleistungstest nach der Anforderung gesucht, der die Extraktionsregel hinzugefügt werden soll. Jedem Ergebnisobjekt wird eine neue Eigenschaft mit dem Namen DeclarativeWebTestItemId hinzugefügt. Diese Eigenschaft wird im Code verwendet, um die richtige Anforderung aus dem Webleistungstest abzurufen.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

## <a name="replace-query-string-parameters"></a>Ersetzen von Abfragezeichenfolgen-Parametern

In diesem Teil des Codebeispiels wird nach allen Abfragezeichenfolgen-Parametern mit dem Namen "ReportSession" gesucht und der Wert in {{SessionId}} geändert:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
---
title: Erstellen eines Webleistungstest-Plug-Ins
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: c4fb207fc5404c0540324a3d32281db14cc6ac65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829309"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Vorgehensweise: Erstellen eines Webleistungstest-Plug-Ins

Webleistungstest-Plug-Ins ermöglichen Ihnen, Code außerhalb der Hauptdeklarationen des Webleistungstests zu isolieren und wiederzuverwenden. Mit einem benutzerdefinierten Webleistungstest-Plug-In können Sie bei Ausführung des Webleistungstests einen Teil des Codes aufrufen. Das Webleistungstest-Plug-In wird bei jeder Testiteration einmal ausgeführt. Wenn Sie außerdem die PreRequest-Methode oder PostRequest-Methode im Test-Plug-In überschreiben, werden diese Anforderungs-Plug-Ins jeweils vor bzw. nach den einzelnen Anforderungen ausgeführt.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Sie können ein benutzerdefiniertes Webleistungstest-Plug-In erstellen, indem Sie die eigene Klasse von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>-Basisklasse ableiten.

Benutzerdefinierte Webleistungstest-Plug-Ins können mit den aufgezeichneten Webleistungstests verwendet werden, sodass Sie nur eine minimale Menge Code erstellen müssen, um eine größere Kontrolle über Ihre Webleistungstests zu erhalten. Sie können die Plug-Ins jedoch auch mit codierten Webleistungstests verwenden. Weitere Informationen finden Sie unter [Generieren und Ausführen eines programmierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Außerdem können Sie Auslastungstest-Plug-Ins erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>So erstellen Sie ein benutzerdefiniertes Webleistungstest-Plug-In

1.  Öffnen Sie ein Webleistungs- und Auslastungstestprojekt, das einen Webleistungstest enthält.

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** und anschließend **Neues Projekt** aus.

     Das Dialogfeld **Neues Projekt hinzufügen** wird angezeigt.

3.  Wählen Sie unter **Installierte Vorlagen** den Eintrag **Visual C#** aus.

4.  Wählen Sie in der Liste der Vorlagen den Eintrag **Klassenbibliothek** aus.

5.  Geben Sie im Textfeld **Name** einen Namen für die Klasse ein.

6.  Klicken Sie auf **OK**.

7.  Das neue Klassenbibliotheksprojekt wird zum **Projektmappen-Explorer** hinzugefügt, und die neue Klasse wird im **Code-Editor** angezeigt.

8.  Klicken Sie im **Projektmappen-Explorer** in der neuen Klassenbibliothek mit der rechten Maustaste auf den Ordner **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

9. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

10. Klicken Sie auf die Registerkarte **.NET**, scrollen Sie nach unten, und klicken Sie auf **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

11. Klicken Sie auf **OK**.

     Der Verweis auf **Microsoft.VisualStudio.QualityTools.WebTestFramework** wird zum Ordner **Verweise** im **Projektmappen-Explorer** hinzugefügt.

12. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten des Webleistungs- und Auslastungstestprojekts, das den Auslastungstest enthält, dem Sie das Webleistungstest-Plug-In hinzufügen möchten. Klicken Sie anschließend auf **Verweis hinzufügen**.

13. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

14. Klicken Sie auf die Registerkarte **Projekte**, und wählen Sie das **Klassenbibliotheksprojekt** aus.

15. Klicken Sie auf **OK**.

16. Schreiben Sie im **Code-Editor** den Code für das Plug-In. Erstellen Sie zunächst eine neue öffentliche Klasse, die von <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> abgeleitet wird.

17. Implementieren Sie Code innerhalb eines oder mehrerer Ereignishandler. Beachten Sie hierzu die Beispielimplementierung im folgenden Abschnitt.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

18. Nachdem Sie den Code verfasst haben, erstellen Sie das neue Projekt.

19. Öffnen Sie einen Webleistungstest.

20. Um das Webleistungstest-Plug-In hinzuzufügen, wählen Sie auf der Symbolleiste **Webtest-Plug-In hinzufügen** aus.

     Das Dialogfeld **Webtest-Plug-In hinzufügen** wird angezeigt.

21. Wählen Sie unter **Plug-In auswählen** die Webleistungstest-Plug-In-Klasse aus.

22. Legen Sie im Bereich **Eigenschaften für das ausgewählte Plug-In** die Anfangswerte fest, die das Plug-In zur Laufzeit verwenden soll.

    > [!NOTE]
    > Sie können beliebig viele Plug-In-Eigenschaften verfügbar machen. Die Eigenschaften müssen dazu lediglich öffentlich, festlegbar und von einem Basistyp (z. B. "Integer", "Boolean" oder "String") sein. Sie können die Eigenschaften des Webleistungstest-Plug-Ins auch zu einem späteren Zeitpunkt im Eigenschaftenfenster ändern.

23. Klicken Sie auf **OK**.

     Das Plug-In wird dem Ordner **Webtest-Plug-Ins** hinzugefügt.

    > [!WARNING]
    > Möglicherweise erhalten Sie eine Fehlermeldung wie die folgende, wenn Sie einen Webleistungstest oder einen Auslastungstest ausführen, der das Plug-In verwendet:
    >
    > **Fehler bei der Anforderung: Ausnahme in \<plug-in>-Ereignis: Die Datei oder Assembly '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' oder eine ihrer Abhängigkeiten konnte nicht geladen werden. Das System konnte die angegebene Datei nicht finden.**
    >
    > Ein solcher Fehler wird verursacht, wenn Sie an einem der Plug-Ins Codeänderungen vornehmen und eine neue DLL-Version **(Version=0.0.0.0)** erstellen, während das Plug-In weiterhin auf die ursprüngliche Plug-In-Version verweist. Um dieses Problem zu beheben, führen Sie folgende Schritte aus:
    >
    > 1.  Im Webleistungs- und Auslastungstestprojekt wird in Verweisen eine Warnung angezeigt. Entfernen Sie den Verweis auf die Plug-In-DLL, und fügen Sie ihn wieder hinzu.
    > 2.  Entfernen Sie das Plug-In aus dem Test oder vom entsprechenden Speicherort, und fügen Sie es dann wieder hinzu.

## <a name="example"></a>Beispiel

Mit dem folgenden Code wird ein benutzerdefiniertes Webleistungstest-Plug-In erstellt, das dem <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> ein Element hinzufügt, das die Testiteration angibt.

Nach der Ausführung des Webleistungstests können Sie mit diesem Plug-In das hinzugefügte Element mit dem Namen **TestIterationNumber** auf der Registerkarte **Kontext** im **Webleistungstest-Ergebnisviewer** anzeigen.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Vorgehensweise: Erstellen eines Anforderungsebenen-Plug-Ins](../test/how-to-create-a-request-level-plug-in.md)
- [Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Vorgehensweise: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
---
title: Webleistungstest-API in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0662f81fe7b26a2da0164c19e9dedb4e0c971f41
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-the-web-performance-test-api"></a>Gewusst wie: Verwenden der Webleistungstest-API

Sie können Code für die Webleistungstests schreiben. Die Webleistungstest-API wird verwendet, um Code für Webleistungstests, Webleistungstest-Plug-Ins, Anforderungs-Plug-Ins, Anforderungen, Extraktions- und Validierungsregeln zu erstellen. Die Klassen, aus denen diese Typen bestehen, sind die Kernklassen in dieser API. Die anderen Typen in dieser API werden verwendet, um die Erstellung folgender Objekte zu unterstützen: <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> und <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Sie verwenden den <xref:Microsoft.VisualStudio.TestTools.WebTesting>-Namespace, um benutzerdefinierte Webleistungstests zu erstellen.

 Sie können auch die Webleistungstest-API verwenden, um deklarative Webleistungstests programmgesteuert zu erstellen und zu speichern. Dazu verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest>-Klasse und die <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>-Klasse.

> [!TIP]
>  Verwenden Sie den Objektkatalog, um den <xref:Microsoft.VisualStudio.TestTools.WebTesting>-Namespace zu durchsuchen. Sowohl der Visual C#- als auch der Visual Basic-Editor bieten IntelliSense-Unterstützung für das Schreiben von Code mit den Klassen im Namespace.

 Sie können auch Plug-Ins für Auslastungstests erstellen. Weitere Informationen finden Sie unter [How to: Use the Load Test API (Vorgehensweise: Verwenden der Auslastungstest-API)](../test/how-to-use-the-load-test-api.md) und [How to: Create a Load Test Plug-In (Vorgehensweise: Erstellen eines Auslastungstest-Plug-Ins)](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>So verwenden Sie den WebTesting-Namespace

1.  Öffnen Sie ein Webleistungs- und Auslastungstestprojekt, das einen Webleistungstest enthält.

2.  Fügen Sie Ihrer Testprojektmappe ein Projekt für eine Visual C#- oder Visual Basic-Klassenbibliothek hinzu.

3.  Fügen Sie dem Webleistungs- und Auslastungstestprojekt einen Verweis auf das Klassenbibliotheksprojekt hinzu.

4.  Fügen Sie im Klassenbibliotheksprojekt einen Verweis auf die DLL-Datei "Microsoft.VisualStudio.QualityTools.WebTestFramework" hinzu.

5.  Fügen Sie der Klassendatei im Klassenbibliothekprojekt eine `using`-Anweisung für den <xref:Microsoft.VisualStudio.TestTools.WebTesting>-Namespace hinzu.

6.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>-Schnittstelle implementiert.

7.  Erstellen Sie das Projekt.

8.  Fügen Sie das neue Webleistungstest-Plug-In mit dem Webleistungstest-Editor hinzu:

    1.  Klicken Sie auf der Symbolleiste auf **Webtest-Plug-In hinzufügen**.

         Das Dialogfeld **Webtest-Plug-In hinzufügen** wird angezeigt.

    2.  Wählen Sie unter **Plug-In auswählen** die Webleistungstest-Plug-In-Klasse aus.

    3.  Legen Sie im Bereich **Eigenschaften für das ausgewählte Plug-In** die Anfangswerte fest, die das Plug-In zur Laufzeit verwenden soll.

        > [!NOTE]
        > Sie können beliebig viele Plug-In-Eigenschaften verfügbar machen. Die Eigenschaften müssen dazu lediglich öffentlich, festlegbar und von einem Basistyp (z. B. "Integer", "Boolean" oder "String") sein. Sie können die Eigenschaften des Webleistungstest-Plug-Ins auch zu einem späteren Zeitpunkt im Eigenschaftenfenster bearbeiten.

    4.  Klicken Sie auf **OK**.

9. Führen Sie den Webleistungstest aus.

     Eine Beispielimplementierung von <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> finden Sie unter [Vorgehensweise: Erstellen eines Webleistungstest-Plug-Ins](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Gewusst wie: Verwenden der Auslastungstest-API](../test/how-to-use-the-load-test-api.md)
- [Gewusst wie: Erstellen eines Webleistungstest-Plug-Ins](../test/how-to-create-a-web-performance-test-plug-in.md)
---
title: 'Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 97bbf8212caf87f28849df15d350811579f22ccd
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325226"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie einen einfachen Windows Communication Foundation (WCF)-Dienst erstellen, testen, und klicken Sie dann eine Windows Forms-Anwendung zugreifen.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Erstellen eines Diensts

1. Öffnen Sie Visual Studio.

::: moniker range="vs-2017"

2. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** >**Projekt**aus.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#**  Knoten, und wählen Sie **WCF**, gefolgt von **WCF-Dienstbibliothek**.

4. Klicken Sie auf **OK**, um das Projekt zu erstellen.

   ![Das WCF-Dienstbibliotheksprojekt](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Typ **Wcf-Dienstbibliothek** in das Suchfeld auf der **Erstellen eines neuen Projekts** Seite. Wählen Sie entweder die C# oder Visual Basic-Vorlage für **WCF-Dienstbibliothek**, und klicken Sie dann auf **Weiter**.

   ![Erstellen Sie neues WCF-Dienstbibliothek-Projekt in Visual Studio-2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Wenn Sie keine Vorlagen nicht angezeigt wird, müssen Sie möglicherweise zum Installieren der **Windows Communication Foundation** Komponente von Visual Studio. Wählen Sie **Weitere Tools und Features installieren** zu Visual Studio-Installer zu öffnen. Wählen Sie die **Einzelkomponenten** Registerkarte, scrollen Sie zum **Entwicklungsaktivitäten**, und wählen Sie dann **Windows Communication Foundation**. Klicken Sie auf **Ändern**.

4. Auf der **konfigurieren Sie das neue Projekt** auf **erstellen**.

::: moniker-end

   > [!NOTE]
   > Dadurch wird ein funktionierender Dienst erstellt, der getestet und aufgerufen werden kann. Die folgenden beiden Schritte veranschaulichen, wie Sie die Standardmethode ändern können, um einen anderen Datentyp zu verwenden. In einer echten Anwendung würden Sie dem Dienst auch Ihre eigenen Funktionen hinzufügen.

5. In **Projektmappen-Explorer**, doppelklicken Sie auf **"IService1.vb"** oder **IService1.cs**.

   ![Die Datei "IService1"](../data-tools/media/wcf2.png)

   Suchen Sie die folgende Zeile:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Ändern Sie den Typ für die `value` Parameter in Zeichenfolge:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   Beachten Sie im obigen Code die `<OperationContract()>`- oder `[OperationContract]`-Attribute. Diese Attribute sind für jede Methode erforderlich, die vom Dienst zur Verfügung gestellt wird.

6. In **Projektmappen-Explorer**, doppelklicken Sie auf **Service1.vb** oder **Service1.cs**.

   ![Die Datei "Service1"](../data-tools/media/wcf3.png)

   Suchen Sie die folgende Zeile:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Ändern Sie den Typ für die `value` Parameter in Zeichenfolge:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testen des Diensts

1. Drücken Sie **F5**, um den Dienst auszuführen. Ein **WCF-Testclient** Formular angezeigt wird, und lädt den Dienst.

2. Doppelklicken Sie im **WCF-Testclient**-Formular auf die **GetData()**-Methode unter **IService1**. Die **GetData** Registerkarte wird angezeigt.

     ![Die GetData&#40; &#41; Methode](../data-tools/media/wcf4.png)

3. Wählen Sie im Feld **Anforderung** das Feld **Wert** aus, und geben Sie `Hello` ein.

     ![Das Wertfeld](../data-tools/media/wcf5.png)

4. Klicken Sie auf die Schaltfläche **Aufrufen**. Wenn eine **Sicherheitswarnung** klicken Sie im angezeigten Dialogfeld **OK**. Das Ergebnis zeigt an, der **Antwort** Feld.

     ![Das Ergebnis im Feld "Antwort"](../data-tools/media/wcf6.png)

5. Klicken Sie im Menü **Datei** auf **Beenden**, um das Testformular zu schließen.

## <a name="access-the-service"></a>Greifen Sie auf den Dienst

### <a name="reference-the-wcf-service"></a>Verweisen auf den WCF-Dienst

1. Zeigen Sie im Menü **Datei** auf die Option **Hinzufügen**, und klicken Sie anschließend auf **Neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#**  Knoten **Windows**, und wählen Sie dann auf  **Windows Forms-Anwendung**. Klicken Sie auf **OK**, um das Projekt zu öffnen.

     ![Windows Forms-Anwendungsprojekt](../data-tools/media/wcf7.png)

3. Klicken Sie mit der rechten Maustaste auf **WindowsApplication1** und dann auf **Dienstverweis hinzufügen**. Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

4. Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.

     ![Das Dialogfeld "Dienstverweis hinzufügen"](../data-tools/media/wcf8.png)

     **"Service1"** zeigt in der **Services** Bereich.

5. Klicken Sie auf **OK**, um den Dienstverweis hinzuzufügen.

### <a name="build-a-client-application"></a>Erstellen Sie eine Clientanwendung

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **Form1.vb** oder **Form1.cs**, um den Windows Forms-Designer zu öffnen, wenn er nicht bereits geöffnet ist.

2. Ziehen Sie aus der **Toolbox** ein `TextBox`-Steuerelement, ein `Label`-Steuerelement und ein `Button`-Steuerelement auf das Formular.

     ![Hinzufügen von Steuerelementen zum Formular](../data-tools/media/wcf9.png)

3. Doppelklicken Sie auf `Button`, und fügen Sie dem `Click`-Ereignishandler den folgenden Code hinzu:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **WindowsApplication1**, und klicken Sie auf **Als Startprojekt festlegen**.

5. Drücken Sie **F5**, um das Projekt auszuführen. Geben Sie Text ein, und klicken Sie auf die Schaltfläche. Zeigt die Bezeichnung "Ihre Eingabe:" und zeigt den Text an, die Sie eingegeben haben.

     ![Das Formular mit dem Ergebnis](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
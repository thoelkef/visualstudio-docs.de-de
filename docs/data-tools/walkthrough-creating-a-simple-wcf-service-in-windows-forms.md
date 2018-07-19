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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2c9d0bd58adcd0a0595c061fa4dfaa81f629601
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174246"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einen einfachen [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]-Dienst erstellen, testen und über eine Windows Forms-Anwendung darauf zugreifen können.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Erstellen Sie den Dienst

### <a name="to-create-a-wcf-service"></a>So erstellen Sie einen WCF-Dienst

1.  Zeigen Sie im Menü **Datei** auf **Neu** , und klicken Sie dann auf **Projekt**.

2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten, und klicken Sie auf **WCF**, gefolgt von **WCF -Dienstbibliothek**. Klicken Sie auf **OK** auf das Projekt zu öffnen.

     ![Das WCF-Dienstbibliotheksprojekt](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Dadurch wird ein funktionierender Dienst erstellt, der getestet und aufgerufen werden kann. Die folgenden beiden Schritte veranschaulichen, wie Sie die Standardmethode ändern können, um einen anderen Datentyp zu verwenden. In einer echten Anwendung würden Sie dem Dienst auch Ihre eigenen Funktionen hinzufügen.

3.  ![Die Datei "IService1"](../data-tools/media/wcf2.png)

     In **Projektmappen-Explorer**, doppelklicken Sie auf **"IService1.vb"** oder **IService1.cs** und suchen Sie die folgende Zeile:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Ändern Sie den Typ für die `value` Parameter in Zeichenfolge:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     Beachten Sie im obigen Code die `<OperationContract()>`- oder `[OperationContract]`-Attribute. Diese Attribute sind für jede Methode erforderlich, die vom Dienst zur Verfügung gestellt wird.

4.  ![Die Datei "Service1"](../data-tools/media/wcf3.png)

     In **Projektmappen-Explorer**, doppelklicken Sie auf **Service1.vb** oder **Service1.cs** und suchen Sie die folgende Zeile:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Ändern Sie den Typ für die `value` Parameter in Zeichenfolge:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testen Sie den Dienst

### <a name="to-test-a-wcf-service"></a>So testen Sie einen WCF-Dienst

1.  Drücken Sie **F5** zum Ausführen des Diensts. Ein **WCF-Testclient** Formular angezeigt wird, und lädt den Dienst.

2.  In der **WCF-Testclient** bilden, doppelklicken Sie auf die **GetData()** Methode unter **IService1**. Die **GetData** Registerkarte wird angezeigt.

     ![Die GetData&#40; &#41; Methode](../data-tools/media/wcf4.png)

3.  In der **anfordern** Kontrollkästchen die **Wert** Feld- und `Hello`.

     ![Das Wertfeld](../data-tools/media/wcf5.png)

4.  Klicken Sie auf die **Invoke** Schaltfläche. Wenn eine **Sicherheitswarnung** klicken Sie im angezeigten Dialogfeld **OK**. Das Ergebnis zeigt an, der **Antwort** Feld.

     ![Das Ergebnis im Feld "Antwort"](../data-tools/media/wcf6.png)

5.  Auf der **Datei** Menü klicken Sie auf **beenden** um das Testformular zu schließen.

## <a name="access-the-service"></a>Greifen Sie auf den Dienst

### <a name="to-reference-a-wcf-service"></a>So greifen Sie auf einen WCF-Dienst zu

1.  Auf der **Datei** Startmenü **hinzufügen** , und klicken Sie dann auf **neues Projekt**.

2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten **Windows**, und wählen Sie dann  **Windows Forms-Anwendung**. Klicken Sie auf **OK** auf das Projekt zu öffnen.

     ![Windows Forms-Anwendungsprojekt](../data-tools/media/wcf7.png)

3.  Mit der rechten Maustaste **WindowsApplication1** , und klicken Sie auf **Hinzufügen eines Dienstverweises**. Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

4.  In der **Hinzufügen eines Dienstverweises** Dialogfeld klicken Sie auf **Discover**.

     ![Das Dialogfeld "Dienstverweis hinzufügen"](../data-tools/media/wcf8.png)

     **"Service1"** zeigt in der **Services** Bereich.

5.  Klicken Sie auf **OK** um den Dienstverweis hinzuzufügen.

### <a name="to-build-a-client-application"></a>So erstellen Sie eine Clientanwendung

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf **Form1.vb** oder **"Form1.cs"** der Windows Forms-Designer zu öffnen, wenn es nicht bereits geöffnet ist.

2.  Von der **Toolbox**, ziehen Sie eine `TextBox` -Steuerelement, ein `Label` -Steuerelement, und ein `Button` -Steuerelement auf das Formular.

     ![Hinzufügen von Steuerelementen zum Formular](../data-tools/media/wcf9.png)

3.  Doppelklicken Sie auf `Button`, und fügen Sie dem `Click`-Ereignishandler den folgenden Code hinzu:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  In **Projektmappen-Explorer**, mit der rechten Maustaste **WindowsApplication1** , und klicken Sie auf **als Startprojekt festlegen**.

5.  Drücken Sie **F5** um das Projekt auszuführen. Geben Sie Text ein, und klicken Sie auf die Schaltfläche. Zeigt die Bezeichnung "Ihre Eingabe:" und zeigt den Text an, die Sie eingegeben haben.

     ![Das Formular mit dem Ergebnis](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
---
title: 'Exemplarische Vorgehensweise: Erstellen einen einfachen WCF-Dienst in Windows Forms | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c2c5fba8914ba3b5404412c0cbc55af36fe15c21
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661037"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einen einfachen [!INCLUDE[vsindigo](../includes/vsindigo-md.md)]-Dienst erstellen, testen und über eine Windows Forms-Anwendung darauf zugreifen können.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Erstellen des Diensts  
  
#### <a name="to-create-a-wcf-service"></a>So erstellen Sie einen WCF-Dienst  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu** , und klicken Sie dann auf **Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual C#**, und klicken Sie anschließend auf **WCF** und dann auf **WCF-Dienstbibliothek**. Klicken Sie auf **OK**, um das Projekt zu öffnen.  
  
     ![Der WCF-Dienstbibliotheksprojekt](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Dadurch wird ein funktionierender Dienst erstellt, der getestet und aufgerufen werden kann. Die folgenden beiden Schritte veranschaulichen, wie Sie die Standardmethode ändern können, um einen anderen Datentyp zu verwenden. In einer echten Anwendung würden Sie dem Dienst auch Ihre eigenen Funktionen hinzufügen.  
  
3.  ![Die Datei "IService1"](../data-tools/media/wcf2.png "wcf2")  
  
     In **Projektmappen-Explorer**, doppelklicken Sie auf IService1.vb oder IService1.cs, und suchen Sie die folgende Zeile:  
  
     [! Code-Csharp [WCFWalkthrough #4] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/IService1 (2).cs 4)] [! Code – Vb [WCFWalkthrough #4] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/IService1 (2).vb 4)]  
  
     Ändern Sie den Typ für den `value`-Parameter in `String`:  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     Beachten Sie im obigen Code die `<OperationContract()>`- oder `[OperationContract]`-Attribute. Diese Attribute sind für jede Methode erforderlich, die vom Dienst zur Verfügung gestellt wird.  
  
4.  ![Die Datei "Service1"](../data-tools/media/wcf3.png "wcf3")  
  
     In **Projektmappen-Explorer**, doppelklicken Sie auf Service1.vb "oder" Service1.cs, und suchen Sie die folgende Zeile:  
  
     [! Code-Csharp [WCFWalkthrough #5] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/Service1 (2).cs 5)] [! Code – Vb [WCFWalkthrough #5] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/Service1 (2).vb 5)]  
  
     Ändern Sie den Typ für den value-Parameter in `String`:  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Testen des Diensts  
  
#### <a name="to-test-a-wcf-service"></a>So testen Sie einen WCF-Dienst  
  
1.  Drücken Sie **F5**, um den Dienst auszuführen. Ein **WCF-Testclient** -Formular wird angezeigt, und den Dienst lädt.  
  
2.  Doppelklicken Sie im **WCF-Testclient**-Formular auf die **GetData()**-Methode unter **IService1**. Die **GetData** Registerkarte wird angezeigt.  
  
     ![Die GetData&#40; &#41; Methode](../data-tools/media/wcf4.png "wcf4")  
  
3.  Wählen Sie im Feld **Anforderung** das Feld **Wert** aus, und geben Sie `Hello` ein.  
  
     ![Das Wertfeld](../data-tools/media/wcf5.png "wcf5")  
  
4.  Klicken Sie auf die Schaltfläche **Aufrufen**. Wenn eine **Sicherheitswarnung** Dialogfeld wird angezeigt, klicken Sie auf **OK**. Das Ergebnis erscheint in der **Antwort** Feld.  
  
     ![Das Ergebnis im Antwortfeld](../data-tools/media/wcf6.png "wcf6")  
  
5.  Klicken Sie im Menü **Datei** auf **Beenden**, um das Testformular zu schließen.  
  
## <a name="accessing-the-service"></a>Zugriff auf den Dienst  
  
#### <a name="to-reference-a-wcf-service"></a>So greifen Sie auf einen WCF-Dienst zu  
  
1.  Zeigen Sie im Menü **Datei** auf die Option **Hinzufügen**, und klicken Sie anschließend auf **Neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten, und wählen **Windows**, und wählen Sie dann auf **Windows Forms-Anwendung**. Klicken Sie auf **OK**, um das Projekt zu öffnen.  
  
     ![Windows Forms-Anwendungsprojekt](../data-tools/media/wcf7.png "wcf7")  
  
3.  Klicken Sie mit der rechten Maustaste auf **WindowsApplication1** und dann auf **Dienstverweis hinzufügen**. Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.  
  
4.  Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.  
  
     ![Das Dialogfeld "Add Service Reference"](../data-tools/media/wcf8.png "wcf8")  
  
     **"Service1"** erscheint in der **Services** Bereich.  
  
5.  Klicken Sie auf **OK**, um den Dienstverweis hinzuzufügen.  
  
#### <a name="to-build-a-client-application"></a>So erstellen Sie eine Clientanwendung  
  
1.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Form1.vb** oder **Form1.cs**, um den Windows Forms-Designer zu öffnen, wenn er nicht bereits geöffnet ist.  
  
2.  Ziehen Sie aus der **Toolbox** ein `TextBox`-Steuerelement, ein `Label`-Steuerelement und ein `Button`-Steuerelement auf das Formular.  
  
     ![Hinzufügen von Steuerelementen zum Formular](../data-tools/media/wcf9.png "wcf9")  
  
3.  Doppelklicken Sie auf `Button`, und fügen Sie dem `Click`-Ereignishandler den folgenden Code hinzu:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **WindowsApplication1**, und klicken Sie auf **Als Startprojekt festlegen**.  
  
5.  Drücken Sie **F5**, um das Projekt auszuführen. Geben Sie Text ein, und klicken Sie auf die Schaltfläche. Zeigt die Bezeichnung "Ihre Eingabe:" und den von Ihnen eingegebenen Text an.  
  
     ![Das Formular mit dem Ergebnis](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

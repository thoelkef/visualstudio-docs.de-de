---
title: "Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8d3d007024cdca160c194285da8f0a741100253d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt
  Sie können Verfügbarmachen von Code in einem [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Projekt in Visual Basic für Applikationen (VBA) Code gegebenenfalls die zwei Arten von Code, die miteinander interagieren.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic-Verfahren unterscheidet sich vom Visual C#-Prozess. Weitere Informationen finden Sie unter [wie: Verfügbarmachen von Code für VBA in einem Visual C &#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Der Prozess ist für Code in einer Hostelementklasse anders, als vielmehr für Code in anderen Klassen:  
  
-   [Verfügbarmachen von Code in einer Hostelementklasse](#HostItemCode)  
  
-   [Verfügbarmachen von Code, der nicht in einer Hostelementklasse ist](#NonHostItem)  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [How Do I: Aufrufen VSTO-Code aus VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a>Verfügbarmachen von Code in einer Hostelementklasse  
 Legen Sie zum Aktivieren von VBA-Code zum Aufrufen von Visual Basic-Code in einer Hostelementklasse der **EnableVbaCallers** -Eigenschaft des Hostelements wird auf **"true"**.  
  
 Eine exemplarische Vorgehensweise, die veranschaulicht, wie eine Methode einer Hostelementklasse verfügbar gemacht, und klicken Sie dann aus VBA aufgerufen wird, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem Visual Basic-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Weitere Informationen zu Hostelementen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Code in ein Hostelement für VBA verfügbar machen.  
  
1.  Öffnen oder erstellen Sie eine Dokumentebene [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Projekt, auf einem Word-Dokument, eine Excel-Arbeitsmappe oder ein Excel-Vorlagen basiert, die Makros unterstützen und bereits VBA-Code enthält.  
  
     Weitere Informationen zu den Dokument-Dateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden, ohne dass der Benutzer zum Aktivieren von Makros aufgefordert werden darf. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.  
  
3.  Fügen Sie die Eigenschaft, eine Methode oder ein Ereignis, das Sie für VBA in eines der Hostelementklassen in Ihrem Projekt verfügbar machen möchten, und deklarieren Sie den neuen Member als **öffentlichen**. Der Name der Klasse hängt von der Anwendung ab:  
  
    -   In einem Word-Projekt die Hostelementklasse wird mit dem Namen `ThisDocument` standardmäßig.  
  
    -   In einem Excel-Projekt die Hostelementklassen heißen `ThisWorkbook`, `Sheet1`, `Sheet2`, und `Sheet3` standardmäßig.  
  
4.  Legen Sie die **EnableVbaCallers** -Eigenschaft für das Hostelement auf **"true"**. Diese Eigenschaft steht in der **Eigenschaften** Fenster, wenn das Hostelement im Designer geöffnet ist.  
  
     Nachdem Sie diese Eigenschaft festlegen, legt Visual Studio automatisch die **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument ist nicht bereits VBA-Code enthält oder wenn VBA-Code im Dokument nicht vertrauenswürdig ist und ausgeführt wird, Sie eine Fehlermeldung, beim Festlegen erhalten der **EnableVbaCallers** Eigenschaft **"true"**. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.  
  
5.  Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung erinnert Sie daran, dass wenn Sie VBA-Code die Arbeitsmappe oder das Dokument beim Hinzufügen des Projekts aus ausgeführt werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], der VBA-Code verloren das nächste Mal Sie das Projekt erstellen. Dies ist, da das Dokument im Buildausgabeordner überschrieben wird, jedes Mal, wenn Sie das Projekt erstellen.  
  
     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufrufen kann. Visual Studio fügt auch eine Eigenschaft namens `CallVSTOAssembly` auf die `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, oder `Sheet3` Modul im VBA-Projekt. Sie können diese Eigenschaft verwenden, auf öffentliche Member der Klasse zugreifen, die Sie für VBA verfügbar gemacht.  
  
6.  Erstellen Sie das Projekt.  
  
##  <a name="NonHostItem"></a>Verfügbarmachen von Code, der nicht in einer Hostelementklasse ist  
 Zum Aktivieren von VBA-Code in Visual Basic-Code aufrufen, die nicht in einer Hostelementklasse befindet, ändern Sie den Code, damit sie für VBA sichtbar sind.  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Um Code verfügbar zu machen, die nicht in einer Hostelementklasse für VBA  
  
1.  Öffnen oder erstellen Sie eine Dokumentebene [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Projekt, auf einem Word-Dokument, eine Excel-Arbeitsmappe oder ein Excel-Vorlagen basiert, die Makros unterstützen und bereits VBA-Code enthält.  
  
     Weitere Informationen zu den Dokument-Dateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden, ohne dass der Benutzer zum Aktivieren von Makros aufgefordert werden darf. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.  
  
3.  Fügen Sie das Element, das Sie zu einer öffentlichen Klasse in Ihrem Projekt für VBA verfügbar machen möchten, und deklarieren Sie den neuen Member als **öffentlichen**.  
  
4.  Übernehmen Sie die folgenden <xref:System.Runtime.InteropServices.ComVisibleAttribute> und <xref:Microsoft.VisualBasic.ComClassAttribute> -Attribute verwenden, um die Klasse, die Sie für VBA verfügbar machen. Diese Attribute machen die Klasse für VBA sichtbar.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Überschreiben Sie die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt, um eine Instanz der Klasse zurückzugeben, die Sie für VBA verfügbar machen. Im folgenden Codebeispiel wird davon ausgegangen, dass Sie eine Klasse mit dem Namen verfügbar machen `DocumentUtilities` für VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Öffnen Sie das Dokument (für Word) oder das Arbeitsblatt (für Excel) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument ist nicht bereits VBA-Code enthält oder wenn VBA-Code im Dokument nicht vertrauenswürdig ist und ausgeführt wird, Sie eine Fehlermeldung, beim Festlegen erhalten der **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"** . Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.  
  
8.  Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung erinnert Sie daran, dass wenn Sie VBA-Code die Arbeitsmappe oder das Dokument beim Hinzufügen des Projekts aus ausgeführt werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], der VBA-Code verloren das nächste Mal Sie das Projekt erstellen. Dies ist, da das Dokument im Buildausgabeordner überschrieben wird, jedes Mal, wenn Sie das Projekt erstellen.  
  
     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufrufen kann. Visual Studio fügt auch eine Methode namens `GetManagedClass` dem VBA-Projekt. Sie können diese Methode aufrufen, von jedem beliebigen Standort in der VBA-Projekt für den Zugriff auf die Klasse, die Sie für VBA verfügbar gemacht.  
  
9. Erstellen Sie das Projekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem Visual Basic-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual C &#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  
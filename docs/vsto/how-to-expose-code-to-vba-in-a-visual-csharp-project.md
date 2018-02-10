---
title: "Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual C#-Projekt | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 1b750137a52d30688f69c825f83f72c7cbeebe45
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual C#-Projekt
  Sie können Code in einem Visual C#-Projekt in Visual Basic für Applikationen (VBA) Code verfügbar machen, wenn Sie möchten, dass die zwei Arten von Code für die Interaktion mit anderen.  
  
 Visual C#-Verfahren unterscheidet sich vom Visual Basic-Verfahren. Weitere Informationen finden Sie unter [wie: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Verfügbarmachen von Code in einem Visual C#-Projekt  
 Um VBA-Code zum Aufrufen von Code in einem Visual C#-Projekt zu aktivieren, ändern Sie den Code, sodass er für COM sichtbar ist, und legen Sie dann die **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"** im Designer.  
  
 Eine exemplarische Vorgehensweise, die zeigt, wie eine Methode aus VBA in einem Visual C#-Projekt aufgerufen wird, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C &#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Code in einem Visual C#-Projekt für VBA verfügbar machen.  
  
1.  Öffnen Sie oder erstellen Sie ein Projekt auf Dokumentebene, die basiert auf einem Word-Dokument, eine Excel-Arbeitsmappe oder ein Excel-Vorlagen, die Makros unterstützen und bereits VBA-Code enthält.  
  
     Weitere Informationen zu den Dokument-Dateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden, ohne dass der Benutzer zum Aktivieren von Makros aufgefordert werden darf. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.  
  
3.  Fügen Sie das Element, das Sie zu einer öffentlichen Klasse in Ihrem Projekt für VBA verfügbar machen möchten, und deklarieren Sie den neuen Member als **öffentlichen**.  
  
4.  Übernehmen Sie die folgenden <xref:System.Runtime.InteropServices.ComVisibleAttribute> und <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attribute verwenden, um die Klasse, die Sie für VBA verfügbar machen. Diese Attribute machen die Klasse für COM sichtbar, generieren aber keine Klassenschnittstelle.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Überschreiben Sie die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt um eine Instanz der Klasse, die Sie verfügbar machen für VBA zurückzugeben:  
  
    -   Wenn Sie eine Hostelementklasse für VBA verfügbar machen, überschreiben die **GetAutomationObject** Methode, die diese Klasse gehört, und die aktuelle Instanz der Klasse zurückzugeben.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Wenn Sie eine Klasse, die sich nicht um ein Hostelement für VBA ist bereitstellen, überschreiben die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt-Element aus, und eine Instanz der Klasse kein Hostelement zurückgeben. Im folgende Code wird beispielsweise davon ausgegangen, dass Sie eine Klasse mit dem Namen verfügbar machen `DocumentUtilities` für VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Weitere Informationen zu Hostelementen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extrahieren Sie eine Schnittstelle, von der Klasse, die Sie für VBA verfügbar machen. In der **Schnittstelle extrahieren** Dialogfeld wählen die öffentlichen Member, die in der Schnittstellendeklaration enthalten sein sollen. Weitere Informationen finden Sie unter [Extract Interface Refactoring](../ide/reference/extract-interface.md).
  
7.  Hinzufügen der **öffentlichen** Schlüsselwort, um die Schnittstellendeklaration.  
  
8.  Die Schnittstelle für COM sichtbar machen, indem das folgende <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attribut der Schnittstelle.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Öffnen Sie das Dokument (für Word) oder das Arbeitsblatt (für Excel) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument ist nicht bereits VBA-Code enthält oder wenn VBA-Code im Dokument nicht vertrauenswürdig ist und ausgeführt wird, Sie eine Fehlermeldung, beim Festlegen erhalten der **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"**. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.  
  
11. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung erinnert Sie daran, dass wenn Sie hinzufügen VBA code in der Arbeitsmappe oder das Dokument beim Ausführen des Projekts aus [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], der VBA-Code verloren beim nächsten des Projekts erstellen. Dies ist, weil das Dokument im Buildausgabeordner ausgegeben, dass jedes Mal überschrieben wird, die Sie das Projekt erstellen.  
  
     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufrufen kann. Visual Studio fügt auch eine Methode namens `GetManagedClass` dem VBA-Projekt. Sie können diese Methode aufrufen, von jedem beliebigen Standort in der VBA-Projekt für den Zugriff auf die Klasse, die Sie für VBA verfügbar gemacht.  
  
12. Erstellen Sie das Projekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C &#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
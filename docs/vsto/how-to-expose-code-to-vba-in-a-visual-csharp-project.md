---
title: 'Vorgehensweise: Verfügbarmachen von Code für VBA in einem C# Projekt'
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f0b3f004f6aebed6426238a081369c7d50e15f5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648508"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Vorgehensweise: Verfügbarmachen von Code für VBA in einem visuellen Objekt C# Projekt
  Sie können Code in einem Visual C#-Projekt in Visual Basic für Applikationen (VBA) Code verfügbar machen, wenn Sie möchten, dass die zwei Arten von Code für die Interaktion mit anderen.  
  
 Der Visual C#-Prozess unterscheidet sich von Visual Basic-Prozess. Weitere Informationen finden Sie unter [Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Verfügbarmachen von Code in einem Visual C#-Projekt  
 Um VBA-Code zum Aufrufen von Code in einem Visual C#-Projekt zu aktivieren, ändern Sie den Code ein, damit er für COM sichtbar ist, und legen Sie die **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"** im Designer.  
  
 Eine exemplarische Vorgehensweise, die zum Aufrufen einer Methode in einem visuellen Objekt veranschaulicht C# aus VBA Projekt, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C#&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Code in einem Visual C#-Projekt für VBA verfügbar machen.  
  
1. Öffnen Sie oder erstellen Sie ein Projekt auf Dokumentebene, die basiert auf einem Word-Dokument, eine Excel-Arbeitsmappe oder ein Excel-Vorlage, die Makros unterstützen und bereits VBA-Code enthält.  
  
    Weitere Informationen zu den Dokument-Dateiformaten, die Makros zu unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.  
  
2. Stellen Sie sicher, dass VBA-Code in das Dokument ohne Aufforderung des Benutzers zum Aktivieren von Makros ausgeführt werden darf. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.  
  
3. Fügen Sie das Element, das für VBA verfügbar machen, um eine öffentliche Klasse in Ihrem Projekt werden sollen, und deklarieren Sie den neuen Member als **öffentliche**.  
  
4. Übernehmen Sie das folgende <xref:System.Runtime.InteropServices.ComVisibleAttribute> und <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribute auf die Klasse, die Sie für VBA verfügbar machen. Diese Attribute machen die Klasse für COM sichtbar, generieren aber keine Klassenschnittstelle.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Überschreiben der **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt um eine Instanz der Klasse, die Sie verfügbar machen für VBA zurückzugeben:  
  
   - Wenn Sie eine Hostelementklasse für VBA verfügbar machen, überschreiben die **GetAutomationObject** Methode, die für diese Klasse gehört, und die aktuelle Instanz der Klasse zurückzugeben.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Wenn Sie eine Klasse, die kein Hostelement für VBA verfügbar sind, überschreiben die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt Element, und eine Instanz der Klasse kein Hostelement zurückgeben. Der folgende Code wird beispielsweise davon ausgegangen, dass Sie eine Klasse, die mit dem Namen verfügbar machen `DocumentUtilities` für VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Weitere Informationen zu Hostelementen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).  
  
6. Extrahieren einer Schnittstelle von der Klasse, die Sie für VBA verfügbar machen. In der **Schnittstelle extrahieren** Dialogfeld wählen die öffentlichen Member, die in der Schnittstellendeklaration enthalten sein sollen. Weitere Informationen finden Sie unter [refactoring des Extrahierens Schnittstelle](../ide/reference/extract-interface.md).
  
7. Hinzufügen der **öffentliche** Schlüsselwort, um die Schnittstellendeklaration.  
  
8. Die Schnittstelle für COM sichtbar zu machen, durch das Hinzufügen der folgenden <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attribut der Schnittstelle.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Öffnen Sie das Dokument (für Word) oder die Arbeitsmappe (für Excel) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument ist nicht bereits VBA-Code enthält, oder ist im Dokument VBA-Code nicht vertrauenswürdig ist und ausgeführt, Sie eine Fehlermeldung beim Festlegen erhalten der **ReferenceAssemblyFromVbaProject** Eigenschaft **"true"**. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.  
  
11. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Nachricht daran erinnert Sie, dass wenn Sie hinzufügen, VBA code für die Arbeitsmappe oder Dokument beim Ausführen des Projekts aus [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], der VBA-Code verloren das nächste Mal, die Sie das Projekt erstellen. Dies ist, da das Dokument im Build ausgegeben, dass jedes Mal überschrieben wird, die Sie das Projekt erstellen.  
  
     An diesem Punkt konfiguriert Visual Studio das Projekt, damit das VBA-Projekt in der Assembly aufrufen kann. Visual Studio fügt auch eine Methode namens `GetManagedClass` auf das VBA-Projekt. Sie können diese Methode aufrufen, von überall aus im VBA-Projekt auf die Klasse zugreifen, die Sie für VBA verfügbar gemacht.  
  
12. Erstellen Sie das Projekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C#&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Vorgehensweise: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
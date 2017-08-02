---
title: "Gewusst wie: Verf&#252;gbarmachen von Code f&#252;r VBA in einem Visual Basic-Projekt"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code"
  - "Verfügbarmachen von Code für VBA"
  - "Hostelemente [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code für VBA"
  - "VBA [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code in Anpassungen auf Dokumentebene"
  - "Visual Basic [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code für VBA"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Verf&#252;gbarmachen von Code f&#252;r VBA in einem Visual Basic-Projekt
  Sie können Code in einem [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Projekt für VBA \(Visual Basic for Applications\)\-Code verfügbar machen, wenn diese beiden Codetypen miteinander interagieren sollen.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Der Visual Basic\-Prozess unterscheidet sich vom Visual C\#\-Prozess.  Weitere Informationen finden Sie unter [Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual C&#35;-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Der Prozess für Code in einer Hostelementklasse unterscheidet sich von dem Prozess für Code in anderen Klassen:  
  
-   [Verfügbarmachen von Code in einer Hostelementklasse](#HostItemCode)  
  
-   [Verfügbarmachen von Code, der sich nicht in einer Hostelementklasse befindet](#NonHostItem)  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [How Do I: Call VSTO Code from VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Verfügbarmachen von Code in einer Hostelementklasse  
 Zum Aktivieren von VBA\-Code für das Aufrufen von Visual Basic\-Code in einer Hostelementklasse legen Sie die **EnableVbaCallers**\-Eigenschaft des Hostelements auf **True** fest.  
  
 Eine exemplarische Vorgehensweise, die zeigt, wie eine Methode einer Hostelementklasse verfügbar gemacht und dann von VBA aufgerufen wird, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual Basic-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  Weitere Informationen zu Hostelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
#### So machen Sie Code in einem Hostelement für VBA verfügbar  
  
1.  Öffnen oder erstellen Sie ein [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Projekt auf Dokumentebene auf der Basis eines Word\-Dokuments, einer Excel\-Arbeitsmappe oder einer Excel\-Vorlage, die Makros unterstützen und bereits VBA\-Code enthalten.  
  
     Weitere Informationen über die Dokumentdateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word\-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass der VBA\-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer Makros aktivieren muss.  Sie können den auszuführenden VBA\-Code als vertrauenswürdig festlegen, indem Sie den Speicherort des Office\-Projekts zur Liste der vertrauenswürdigen Speicherorte in den Einstellungen für das Sicherheitscenter für Word oder Excel hinzufügen.  
  
3.  Fügen Sie die Eigenschaft, die Methode oder das Ereignis, die bzw. das Sie für VBA verfügbar machen möchten, zu einer der Hostelementklassen im Projekt hinzu, und deklarieren Sie den neuen Member als **Public**.  Der Name der Klasse hängt von der Anwendung ab:  
  
    -   In einem Word\-Projekt ist der Name der Hostelementklasse standardmäßig `ThisDocument`.  
  
    -   In einem Excel\-Projekt werden für Hostelementklassen standardmäßig die Namen `ThisWorkbook`, `Sheet1`, `Sheet2` und `Sheet3` verwendet.  
  
4.  Legen Sie die **EnableVbaCallers**\-Eigenschaft für das Hostelement auf **True** fest.  Diese Eigenschaft ist im **Eigenschaftenfenster** verfügbar, wenn das Hostelement im Designer geöffnet ist.  
  
     Nachdem Sie diese Eigenschaft festgelegt haben, legt Visual Studio die **ReferenceAssemblyFromVbaProject**\-Eigenschaft automatisch auf **True** fest.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument keinen VBA\-Code enthält oder der VBA\-Code im Dokument nicht vertrauenswürdig ist und deshalb nicht ausgeführt werden kann, wird beim Festlegen der **EnableVbaCallers**\-Eigenschaft auf **True** eine Fehlermeldung angezeigt.  Der Grund hierfür ist, dass Visual Studio das VBA\-Projekt in diesem Fall nicht im Dokument ändern kann.  
  
5.  Klicken Sie in der angezeigten Meldung auf **OK**.  Diese Meldung erinnert Sie daran, dass, wenn Sie VBA\-Code zur Arbeitsmappe oder zum Dokument hinzufügen, während das Projekt von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausgeführt wird, der VBA\-Code verloren geht, wenn Sie das Projekt das nächste Mal erstellen.  Das liegt daran, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.  
  
     Jetzt konfiguriert Visual Studio das Projekt so, dass das VBA\-Projekt die Assembly aufrufen kann.  Visual Studio fügt auch eine Eigenschaft mit dem Namen `CallVSTOAssembly` zum Modul `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2` oder `Sheet3` im VBA\-Projekt hinzu.  Sie können diese Eigenschaft verwenden, um auf öffentliche Member der Klasse zuzugreifen, die Sie für VBA verfügbar gemacht haben.  
  
6.  Erstellen Sie das Projekt.  
  
##  <a name="NonHostItem"></a> Verfügbarmachen von Code, der sich nicht in einer Hostelementklasse befindet  
 Zum Aktivieren von VBA\-Code für das Aufrufen von Visual Basic\-Code, der sich nicht in einer Hostelementklasse befindet, bearbeiten Sie den Code, sodass er für VBA sichtbar ist.  
  
#### So machen Sie Code, der sich nicht in einer Hostelementklasse befindet, für VBA verfügbar  
  
1.  Öffnen oder erstellen Sie ein [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Projekt auf Dokumentebene auf der Basis eines Word\-Dokuments, einer Excel\-Arbeitsmappe oder einer Excel\-Vorlage, die Makros unterstützen und bereits VBA\-Code enthalten.  
  
     Weitere Informationen über die Dokumentdateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word\-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass der VBA\-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer Makros aktivieren muss.  Sie können den auszuführenden VBA\-Code als vertrauenswürdig festlegen, indem Sie den Speicherort des Office\-Projekts zur Liste der vertrauenswürdigen Speicherorte in den Einstellungen für das Sicherheitscenter für Word oder Excel hinzufügen.  
  
3.  Fügen Sie den Member, den Sie für VBA verfügbar machen möchten, zu einer öffentlichen Klasse im Projekt hinzu, und deklarieren Sie den neuen Member als **public**.  
  
4.  Wenden Sie das folgende <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut und <xref:Microsoft.VisualBasic.ComClassAttribute>\-Attribut für die Klasse an, die Sie für VBA verfügbar machen.  Diese Attribute machen die Klasse für VBA sichtbar.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Überschreiben Sie die **GetAutomationObject**\-Methode einer Hostelementklasse im Projekt, um eine Instanz der Klasse zurückzugeben, die Sie für VBA verfügbar machen.  Im folgenden Code wird angenommen, dass Sie eine Klasse mit dem Namen `DocumentUtilities` für VBA verfügbar machen.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Öffnen Sie das Dokument \(für Word\) oder das Arbeitsblatt \(für Excel\) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Wählen Sie im **Eigenschaftenfenster** die **ReferenceAssemblyFromVbaProject**\-Eigenschaft aus, und ändern Sie den Wert in **True**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument noch keinen VBA\-Code enthält oder der VBA\-Code im Dokument nicht vertrauenswürdig ist und deshalb nicht ausgeführt werden kann, wird beim Festlegen der **ReferenceAssemblyFromVbaProject**\-Eigenschaft auf **True** eine Fehlermeldung angezeigt.  Der Grund hierfür ist, dass Visual Studio das VBA\-Projekt in diesem Fall nicht im Dokument ändern kann.  
  
8.  Klicken Sie in der angezeigten Meldung auf **OK**.  Diese Meldung erinnert Sie daran, dass, wenn Sie VBA\-Code zur Arbeitsmappe oder zum Dokument hinzufügen, während das Projekt von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausgeführt wird, der VBA\-Code verloren geht, wenn Sie das Projekt das nächste Mal erstellen.  Das liegt daran, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.  
  
     Jetzt konfiguriert Visual Studio das Projekt so, dass das VBA\-Projekt die Assembly aufrufen kann.  Visual Studio fügt dem VBA\-Projekt außerdem eine Methode mit dem Namen `GetManagedClass` hinzu.  Sie können diese Methode von jedem beliebigen Punkt im VBA\-Projekt aufrufen, um auf die Klasse zuzugreifen, die für VBA verfügbar gemacht wurde.  
  
9. Erstellen Sie das Projekt.  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual Basic-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual C&#35;-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  
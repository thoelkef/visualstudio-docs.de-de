---
title: "Gewusst wie: Verf&#252;gbarmachen von Code f&#252;r VBA in einem Visual C#-Projekt"
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
  - "VBA [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code in Anpassungen auf Dokumentebene"
  - "Visual C# [Office-Entwicklung in Visual Studio], Verfügbarmachen von Code für VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Verf&#252;gbarmachen von Code f&#252;r VBA in einem Visual C#-Projekt
  Sie können Code in einem Visual C\#\-Projekt für VBA \(Visual Basic for Applications\)\-Code verfügbar machen, wenn diese beiden Codetypen miteinander interagieren sollen.  
  
 Der Visual C\#\-Prozess unterscheidet sich vom Visual Basic\-Prozess.  Weitere Informationen finden Sie unter [Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Verfügbarmachen von Code in einem Visual C\#\-Projekt  
 Zum Aktivieren von VBA\-Code für das Aufrufen von Code in einem Visual C\#\-Projekt ändern Sie den Code, sodass er in COM angezeigt wird, und legen Sie dann im Designer die **ReferenceAssemblyFromVbaProject**\-Eigenschaft auf **True** fest.  
  
 Eine exemplarische Vorgehensweise, die das Aufrufen einer Methode in einem Visual C\#\-Projekt von VBA veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C&#35;-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### So machen Sie Code in einem Visual C\#\-Projekt für VBA verfügbar  
  
1.  Öffnen oder erstellen Sie ein Projekt auf Dokumentebene auf der Basis eines Word\-Dokuments, einer Excel\-Arbeitsmappe oder einer Excel\-Vorlage, die Makros unterstützen und bereits VBA\-Code enthalten.  
  
     Weitere Informationen über die Dokumentdateiformate, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Diese Funktion kann in Word\-Vorlagenprojekten nicht verwendet werden.  
  
2.  Stellen Sie sicher, dass der VBA\-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer Makros aktivieren muss.  Sie können den auszuführenden VBA\-Code als vertrauenswürdig festlegen, indem Sie den Speicherort des Office\-Projekts zur Liste der vertrauenswürdigen Speicherorte in den Einstellungen für das Sicherheitscenter für Word oder Excel hinzufügen.  
  
3.  Fügen Sie den Member, den Sie für VBA verfügbar machen möchten, zu einer öffentlichen Klasse im Projekt hinzu, und deklarieren Sie den neuen Member als **public**.  
  
4.  Übernehmen Sie das folgende <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut und <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>\-Attribut für die Klasse, die Sie für VBA verfügbar machen.  Diese Attribute machen die Klasse in COM sichtbar, generieren aber keine Klassenschnittstelle.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Überschreiben Sie die **GetAutomationObject**\-Methode einer Hostelementklasse im Projekt, um eine Instanz der Klasse zurückzugeben, die Sie für VBA verfügbar machen:  
  
    -   Wenn Sie eine Hostelementklasse für VBA verfügbar machen, überschreiben Sie die zu dieser Klasse gehörende **GetAutomationObject**\-Methode, und geben Sie die aktuelle Instanz der Klasse zurück.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Wenn Sie eine Klasse für VBA verfügbar machen, die kein Hostelement ist, überschreiben Sie die **GetAutomationObject**\-Methode eines beliebigen Hostelements im Projekt, und geben Sie eine Instanz der Klasse zurück, die kein Hostelement ist.  Im folgenden Code wird beispielsweise angenommen, dass Sie eine Klasse mit dem Namen `DocumentUtilities` für VBA verfügbar machen.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Weitere Informationen zu Hostelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extrahieren Sie eine Schnittstelle aus der Klasse, die Sie für VBA verfügbar machen.  Wählen Sie im Dialogfeld **Schnittstelle extrahieren** die öffentlichen Member aus, die Sie in die Schnittstellendeklaration aufnehmen möchten.  Weitere Informationen finden Sie unter [Extract Interface Refactoring &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md).  
  
7.  Fügen Sie das **public**\-Schlüsselwort zur Schnittstellendeklaration hinzu.  
  
8.  Machen Sie die Schnittstelle in COM sichtbar, indem Sie das folgende <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut zur Schnittstelle hinzufügen.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Öffnen Sie das Dokument \(für Word\) oder das Arbeitsblatt \(für Excel\) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Wählen Sie im **Eigenschaftenfenster** die **ReferenceAssemblyFromVbaProject**\-Eigenschaft aus, und ändern Sie den Wert in **True**.  
  
    > [!NOTE]  
    >  Wenn die Arbeitsmappe oder das Dokument keinen VBA\-Code enthält oder der VBA\-Code im Dokument nicht vertrauenswürdig ist und deshalb nicht ausgeführt werden kann, wird beim Festlegen der **ReferenceAssemblyFromVbaProject**\-Eigenschaft auf **True** eine Fehlermeldung angezeigt.  Der Grund hierfür ist, dass Visual Studio das VBA\-Projekt in diesem Fall nicht im Dokument ändern kann.  
  
11. Klicken Sie in der angezeigten Meldung auf **OK**.  Diese Meldung erinnert Sie daran, dass, wenn Sie VBA\-Code zur Arbeitsmappe oder zum Dokument hinzufügen, während das Projekt von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausgeführt wird, der VBA\-Code verloren geht, wenn Sie das Projekt das nächste Mal erstellen.  Der Grund hierfür ist, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.  
  
     Jetzt konfiguriert Visual Studio das Projekt so, dass das VBA\-Projekt die Assembly aufrufen kann.  Visual Studio fügt dem VBA\-Projekt außerdem eine Methode mit dem Namen `GetManagedClass` hinzu.  Sie können diese Methode von jedem beliebigen Punkt im VBA\-Projekt aufrufen, um auf die Klasse zuzugreifen, die für VBA verfügbar gemacht wurde.  
  
12. Erstellen Sie das Projekt.  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code von VBA in einem Visual C&#35;-Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Gewusst wie: Verfügbarmachen von Code für VBA in einem Visual Basic-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
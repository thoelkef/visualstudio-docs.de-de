---
title: "Debugging ClickOnce Applications That Use System.Deployment.Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, debugging"
  - "debugging, ClickOnce applications"
  - "debugging, System.Deployment"
  - "deploying applications [ClickOnce], debugging"
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Debugging ClickOnce Applications That Use System.Deployment.Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] können Sie mit der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung konfigurieren, wie eine Anwendung aktualisiert wird.  Wenn Sie jedoch die erweiterten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsfeatures verwenden und anpassen möchten, müssen Sie auf das Bereitstellungsobjektmodell zugreifen, das von <xref:System.Deployment.Application> bereitgestellt wird.  Sie können die <xref:System.Deployment.Application>\-APIs u. a. für die folgenden erweiterten Aufgaben verwenden:  
  
-   Erstellen einer "Jetzt Aktualisieren"\-Option in der Anwendung  
  
-   Bedingte, bedarfsabhängige Downloads verschiedener Anwendungskomponenten  
  
-   Direkt in die Anwendung integrierte Updates  
  
-   Garantieren, dass die Clientanwendung immer auf dem aktuellen Stand ist  
  
 Da die <xref:System.Deployment.Application>\-APIs nur funktionieren, wenn eine Anwendung mithilfe der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Technologie bereitgestellt wird, können Sie sie nur debuggen, indem Sie die Anwendung mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellen, einen Debugger an die Anwendung anhängen und sie dann debuggen.  Es kann sehr schwierig sein, den Debugger rechtzeitig anzuhängen, da der Code oftmals beim Anwendungsstart ausgeführt wird, bevor Sie es schaffen, den Debugger anzuhängen.  Sie können vor dem Updateüberprüfungscode oder dem Code für bedarfsabhängige Downloads break\-Anweisungen einzufügen \(bzw. stop\-Anweisungen in Visual Basic\-Projekten\).  
  
 Folgendes Debugverfahren wird empfohlen:  
  
1.  Stellen Sie vor dem Start sicher, dass die Symboldateien \(.pdb\) und die Quelldateien archiviert sind.  
  
2.  Stellen Sie Version 1 der Anwendung bereit.  
  
3.  Erstellen Sie eine neue leere Projektmappe.  Klicken Sie im Menü **Datei** zuerst auf **Neu** und dann auf **Projekt**.  Öffnen Sie im Dialogfeld **Neues Projekt** den Knoten **Andere Projekttypen**, und wählen Sie anschließend den Ordner **Visual Studio\-Projektmappen** aus.  Wählen Sie im Bereich **Vorlagen** die Option **Leere Projektmappe**.  
  
4.  Fügen Sie den Eigenschaften der neuen Projektmappe den Speicherort der archivierten Quellen hinzu.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektmappenknoten, und klicken Sie dann auf **Eigenschaften**.  Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Quelldateien debuggen**, und fügen Sie das Verzeichnis mit dem archivierten Quellcode hinzu.  Ansonsten findet der Debugger die veralteten Quelldateien, da die Quelldateipfade in der PDB\-Datei aufgezeichnet werden.  Wenn der Debugger veraltete Quelldateien verwendet, wird eine Meldung angezeigt, die Sie darüber informiert, dass die Quelle nicht passend ist.  
  
5.  Stellen Sie sicher, dass der Debugger die PDB\-Dateien finden kann.  Wenn Sie sie mit der Anwendung bereitgestellt haben, werden sie vom Debugger automatisch gefunden.  Der Debugger sucht immer zuerst neben der fraglichen Assembly.  Andernfalls müssen Sie den Archivpfad zu **Speicherorte für Symboldateien \(.pdb\)** hinzufügen \(um auf diese Option zuzugreifen, klicken Sie im Menü **Extras** auf **Optionen**, öffnen Sie dann den Knoten **Debuggen**, und klicken Sie auf **Symbole**\).  
  
6.  Debuggen Sie den gesamten Code zwischen dem `CheckForUpdate`\-Methodenaufruf und den `Download`\/`Update`\-Methodenaufrufen.  
  
     Der Aktualisierungscode könnte z. B. folgendermaßen aussehen:  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  Stellen Sie Version 2 bereit.  
  
8.  Versuchen Sie, den Debugger an die Version 1\-Anwendung anzufügen, da auf diese Weise ein Update für Version 2 heruntergeladen wird.  Alternativ dazu können Sie die `System.Diagnostics.Debugger.Break`\-Methode verwenden oder in Visual Basic einfach `Stop`.  Natürlich sollten Sie diese Methodenaufrufe aus dem Produktionscode entfernen.  
  
     Angenommen, Sie entwickeln eine Windows Forms\-Anwendung und verfügen über einen Ereignishandler für diese Methode mit der Aktualisierungslogik.  Hängen Sie zum Debuggen einfach vor dem Drücken der Taste den Debugger an, und legen Sie anschließend einen Haltepunkt fest \(stellen Sie sicher, dass Sie die passende archivierte Datei öffnen, und den Haltepunkt dort festlegen\).  
  
 Verwenden Sie die <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>\-Eigenschaft, um die <xref:System.Deployment.Application>\-APIs nur dann aufzurufen, wenn die Anwendung bereitgestellt wird. Die APIs sollten nicht beim Debuggen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden.  
  
## Siehe auch  
 <xref:System.Deployment.Application>
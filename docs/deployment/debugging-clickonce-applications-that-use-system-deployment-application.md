---
title: Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: cc4d2a778449be4cbb441397c0a5a427ef91e8dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung können Sie konfigurieren, wie eine Anwendung aktualisiert wird. Wenn Sie verwenden und anpassen müssen jedoch eine erweiterte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsfeatures, müssen die Bereitstellung-Objektmodell bereitgestellt werden, indem Sie den Zugriff auf <xref:System.Deployment.Application>. Sie können die <xref:System.Deployment.Application> -APIs für erweiterte Aufgaben wie z. B.:  
  
-   Erstellen eine Option "Jetzt aktualisieren" in der Anwendung  
  
-   Bedingt, bei Bedarf heruntergeladen, der verschiedenen Anwendungskomponenten  
  
-   Updates, die direkt in die Anwendung integriert  
  
-   Um zu garantieren, dass die Clientanwendung immer auf dem neuesten Stand ist.  
  
 Da die <xref:System.Deployment.Application> APIs funktionieren nur, wenn eine Anwendung mit bereitgestellt wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Technologie, die einzige Möglichkeit, diese zu Debuggen ist zum Bereitstellen der Anwendung über [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], fügen Sie ihm dann debuggen. Es kann schwierig sein, den Debugger anfügen früh genug, da dieser Code häufig ausgeführt wird, wenn die Anwendung gestartet und ausgeführt wird, bevor Sie den Debugger anfügen können. Eine Lösung darin, Seitenumbrüche (oder beendet wird, die für Visual Basic-Projekte) vor dem Update Kontrollkästchen Code oder Code bei Bedarf zu speichern.  
  
 Die empfohlene Debugverfahren lautet wie folgt:  
  
1.  Bevor Sie beginnen, stellen Sie sicher, dass die Symboldateien (.pdb) und Quelldateien archiviert werden.  
  
2.  Bereitstellen Sie Version 1 der Anwendung.  
  
3.  Erstellen Sie eine neue leere Projektmappe. Aus der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**. In der **neues Projekt** öffnen Sie im Dialogfeld die **andere Projekttypen** Knoten, wählen Sie dann die **Visual Studio-Projektmappen** Ordner. In der **Vorlagen** klicken Sie im Bereich **leere Projektmappe**.  
  
4.  Die Eigenschaften für diese neue Lösung archivierten Quellspeicherort hinzugefügt. In **Projektmappen-Explorer**Sie mit der rechten Maustaste des Knotens Projektmappe, und klicken Sie auf **Eigenschaften**. In der **Eigenschaftenseiten** wählen Sie im Dialogfeld **Quelldateien debuggen**, fügen Sie dann das Verzeichnis der archivierten Quellcode hinzu. Hingegen wird der Debugger die veralteten doch Quelldateien finden, da die quelldateipfaden in die PDB-Datei aufgezeichnet werden. Wenn der Debugger veraltete Quelldateien verwendet wird, sehen Sie eine Meldung angezeigt, die die Quelle stimmt nicht überein.  
  
5.  Stellen Sie sicher, dass der Debugger die PDB-Dateien finden kann. Wenn Sie sie mit der Anwendung bereitgestellt haben, sucht der Debugger diese automatisch. Es sucht immer neben der Assembly fraglichen zuerst. Andernfalls müssen Sie das Archivpfad zum hinzuzufügenden der **Symbol Speicherorte für Symboldateien (.pdb)** (auf diese Option aus der **Tools** Menü klicken Sie auf **Optionen**, öffnen Sie dann die  **Debuggen** Knoten, und klicken Sie auf **Symbole**).  
  
6.  Debuggen, was geschieht, zwischen den `CheckForUpdate` und `Download` / `Update` Methodenaufrufe.  
  
     Der Update-Code könnte beispielsweise folgendermaßen aussehen:  
  
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
  
7.  Stellen Sie Version 2.  
  
8.  Es wurde versucht, den Debugger an Version 1 der Anwendung anzuhängen, während des downloads ein Update für Version 2. Alternativ können Sie die `System.Diagnostics.Debugger.Break` Methode oder einfach `Stop` in Visual Basic. Natürlich sollten Sie nicht diese Methodenaufrufe im Produktionscode lassen.  
  
     Nehmen wir beispielsweise an, Sie eine Windows Forms-Anwendung entwickeln und Sie einen Ereignishandler für diese Methode mit der Aktualisierungslogik darin haben. Um dieses Problem behoben werden, einfach anfügen, bevor die Schaltfläche gedrückt, und Sie einen Haltepunkt legen (Stellen Sie sicher, dass die entsprechende archivierte Datei öffnen und dort den Haltepunkt festlegen).  
  
 Verwenden der <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> Eigenschaft zum Aufrufen der <xref:System.Deployment.Application> APIs nur, wenn die Anwendung bereitgestellt wird; die APIs nicht aufgerufen werden soll während des Debuggens [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application>
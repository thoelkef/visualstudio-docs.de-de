---
title: "MSBuild Error MSB3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3190
**MSB3190: ClickOnce unterstützt die angeforderte Ausführungsebene '\< Ebene \>' nicht.**  
  
 Dieser Fehler wird auf Computern mit Windows Vista generiert, wenn das Benutzerkontensteuerungsmanifest \(UAC\) angibt, dass eine ClickOnce\-Anwendung mit Administratorrechten ausgeführt werden muss.  Für ClickOnce und COM ohne Registrierung ist ein externes Manifest erforderlich, in dem angegeben ist, dass die Anwendung als aktueller Benutzer ausgeführt wird.  
  
 ClickOnce akzeptiert nicht die Ausführungsebene `requireAdministrator` oder `highestAvailable`.  Wenn Sie eine dieser Ebenen angeben, erhalten Sie diese Fehlermeldung.  ClickOnce benötigt `asInvoker`, akzeptiert jedoch auch keinen `<requestedExecutionLevel>`\-Knoten, der die Datei\-\/Registrierungsvirtualisierung festlegt. \(Dies bedeutet, dass aus Gründen der Abwärtskompatiblität kein Manifest generiert wird.\)  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So beheben Sie diesen Fehler  
  
-   Generieren Sie ein externes UAC\-Manifest \(app.manifest\), das angibt, dass die Anwendung als aktueller Benutzer ausgeführt werden soll \(`asInvoker`\).  
  
     Rufen Sie in Visual C\#\-Projekten die Seite **Anwendung** des Projekt\-Designers auf, und klicken Sie in der Liste **Manifest** auf **Properties\\app.manifest**.  Weitere Informationen finden Sie unter [Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
     Rufen Sie in Visual Basic\-Projekten die Seite **Anwendung** des Projekt\-Designers auf, und klicken Sie auf **Einstellungen für die Benutzerkontensteuerung anzeigen**.  Hierdurch wird app.manifest für die Bearbeitung geöffnet.  Bearbeiten Sie das folgende Tag im Manifest wie folgt:  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     Weitere Informationen finden Sie unter [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
-   Weitere Informationen zum Generieren eines UAC\-Manifests und Festlegen der Ausführungsebene finden Sie unter [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md).  
  
## Siehe auch  
 [Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)
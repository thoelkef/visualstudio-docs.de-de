---
title: "Deploying ClickOnce Applications For Testing and Production Servers without Resigning | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "ClickOnce applications, deploying without resigning"
  - "ClickOnce deployment, without resigning"
  - "application updates, ClickOnce"
  - "update location [ClickOnce]"
  - "deploymentProvider tag"
  - "manifests [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying ClickOnce Applications For Testing and Production Servers without Resigning
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird ein neues Feature von ClickOnce erläutert, das in .NET Framework, Version 3.5, eingeführt wird. Dieses Feature ermöglicht die Bereitstellung von ClickOnce\-Anwendungen von mehreren Netzwerkspeicherorten aus, ohne dass die ClickOnce\-Manifeste neu signiert oder geändert werden müssen.  
  
> [!NOTE]
>  Das erneute Signieren ist immer noch die bevorzugte Methode zum Bereitstellen neuer Versionen von Anwendungen.  Verwenden Sie nach Möglichkeit diese Methode.  Weitere Informationen finden Sie unter [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
 Drittanbieterentwickler und ISVs können dieses Feature übernehmen und ihren Kunden damit das Aktualisieren von Anwendungen bedeutend erleichtern.  Dieses Feature kann in den folgenden Situationen verwendet werden:  
  
-   Beim Aktualisieren von Anwendungen, jedoch nicht bei der Erstinstallation von Anwendungen.  
  
-   Wenn nur eine Konfiguration einer Anwendung auf einem Computer vorliegt.  Sie können dieses Feature nicht verwenden, wenn die Konfiguration einer Anwendung z. B. auf zwei verschiedene Datenbanken verweist.  
  
## Ausschließen von deploymentProvider aus Bereitstellungsmanifesten  
 In .NET Framework 2.0 und .NET Framework 3.0 muss jede ClickOnce\-Anwendung, die für Offlineverfügbarkeit auf dem System installiert wird, in ihrem Bereitstellungsmanifest einen `deploymentProvider` angeben.  Der `deploymentProvider` wird oft als Updatepfad bezeichnet. Hier sucht ClickOnce nach Anwendungsupdates.  Diese Anforderung sowie die Tatsache, dass Anwendungsherausgeber ihre Bereitstellungen signieren müssen, erschweren Unternehmen das Aktualisieren von ClickOnce\-Anwendungen, die sie von Herstellern oder Drittanbietern erhalten haben.  Hierdurch wird auch die Bereitstellung einer Anwendung von mehreren Speicherorten in demselben Netzwerk aus erschwert.  
  
 Durch die an ClickOnce in .NET Framework 3.5 vorgenommenen Änderungen kann ein Drittanbieter einem Unternehmen nun eine ClickOnce\-Anwendung zur Verfügung stellen, und das Unternehmen kann die Anwendung dann auf seinem Netzwerk bereitstellen.  
  
 Damit dieses Feature eingesetzt werden kann, müssen Entwickler von ClickOnce\-Anwendungen den `deploymentProvider` aus ihren Bereitstellungsmanifesten ausschließen.  Bei der Erstellung von Bereitstellungsmanifesten mit Mage.exe muss das `-providerUrl`\-Argument ausgeschlossen werden. Bei der Generierung von Bereitstellungsmanifesten mit MageUI.exe muss das Textfeld **Startspeicherort** auf der Registerkarte **Anwendungsmanifest** leer gelassen werden.  
  
## deploymentProvider und Anwendungsupdates  
 Ab .NET Framework 3.5 müssen Sie zum Bereitstellen einer ClickOnce\-Anwendung für die Online\- und Offlineverwendung keinen `deploymentProvider` mehr im Bereitstellungsmanifest angeben.  Hiermit wird unterstützt, dass Sie die Bereitstellung selbst verpacken und signieren, aber anderen Unternehmen erlauben, die Anwendung über ihre Netzwerke bereitzustellen.  
  
 Es ist wichtig zu wissen, dass bei Anwendungen ohne `deploymentProvider` der Installationsspeicherort während eines Updates nicht geändert werden kann, es sei denn, das Update enthält wieder einen `deploymentProvider`\-Tag.  
  
 Nachstehend wird dieser Punkt anhand von zwei Beispielen erläutert.  Im ersten Beispiel veröffentlichen Sie eine ClickOnce\-Anwendung, die keinen `deploymentProvider`\-Tag enthält. Benutzer können die Anwendung von http:\/\/www.adatum.com\/MyApplication\/ aus installieren.  Wenn Sie das nächste Update für die Anwendung von http:\/\/subdomain.adatum.com\/MyApplication\/ aus veröffentlichen möchten, gibt es keine Möglichkeit, dies in dem unter http:\/\/www.adatum.com\/MyApplication\/ gespeicherten Bereitstellungsmanifest anzugeben.  Sie haben folgende Möglichkeiten:  
  
-   Bitten Sie Benutzer, die vorherige Version zu deinstallieren und die neue Version vom neuen Speicherort zu installieren.  
  
-   Stellen Sie unter http:\/\/www.adatum.com\/MyApplication\/ ein Update zur Verfügung, das einen `deploymentProvider` einschließt, der auf http:\/\/www.adatum.com\/MyApplication\/ verweist.  Veröffentlichen Sie später ein weiteres Update, in dem `deploymentProvider` auf http:\/\/subdomain.adatum.com\/MyApplication\/ verweist.  
  
 Im zweiten Beispiel veröffentlichen Sie eine ClickOnce\-Anwendung, in der ein `deploymentProvider` angegeben ist. Sie entscheiden sich im Nachhinein, ihn zu entfernen.  Nachdem die neue Version ohne `deploymentProvider` von Kunden heruntergeladen wurde, können Sie den für Updates verwendeten Pfad nicht umleiten. Dazu müssen Sie erst eine Anwendungsversion veröffentlichen, in der der `deploymentProvider` wiederhergestellt ist.  Wie beim ersten Beispiel muss `deploymentProvider` zunächst auf den aktuellen Updatepfad und nicht auf den neuen Pfad verweisen.  Wenn Sie in diesem Fall versuchen, einen `deploymentProvider` einzufügen, der sich auf http:\/\/subdomain.adatum.com\/MyApplication\/ bezieht, tritt beim nächsten Update ein Fehler auf.  
  
## Erstellen einer Bereitstellung  
 Schrittweise Anweisungen zum Erstellen von Bereitstellungen, die von verschiedenen Netzwerkstandorten aus bereitgestellt werden können, finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## Siehe auch  
 [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)
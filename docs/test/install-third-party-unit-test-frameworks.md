---
title: "Installieren von Frameworks f&#252;r Komponententests von Drittanbietern | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "mlearned"
manager: "douge"
---
# Installieren von Frameworks f&#252;r Komponententests von Drittanbietern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Visual Studio\-Test\-Explorer kann jedes beliebige Framework für Komponententests ausgeführt werden, für den eine Adapterschnittstelle für den Explorer entwickelt wurde.  Das Installationsprogramm des Frameworks installiert die Binarys und fügt Visual Studio\-Projektvorlagen für die von ihm unterstützten Sprachen hinzu.  Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test\-Explorer registriert.  Eine Visual Studio\-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen.  Der Test\-Explorer kann sie alle ausführen.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## Erwerb von Drittanbieter\-Frameworks  
 Sie können viele Komponententest\-Frameworks von Drittanbietern oder aus der Visual Studio Gallery auf der MSDN\-Website herunterladen und mithilfe des Visual Studio\-Erweiterungs\-Managers installieren.  Frameworks können außerdem von anderen Websites, wie etwa der Website des Frameworks, heruntergeladen werden.  
  
### Installieren in Visual Studio  
  
1.  Wählen Sie im Standardmenü **Tools** und dort **Erweiterungen und Updates** aus.  
  
2.  Erweitern Sie **Online**, **Visual Studio Gallery**, **Tools**.  Wählen Sie **Test** aus.  
  
3.  Suchen Sie das Framework in der Liste.  
  
4.  Wählen Sie das Framework und dann **Herunterladen** aus.  
  
 Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio\-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
### Installation aus dem Web  
 Wenn Sie das Framework kennen, für das Sie sich interessieren:  
  
1.  Öffnen Sie [Visual Studio\-Downloads](http://go.microsoft.com/fwlink/?LinkId=236267) auf der MSDN\-Website.  
  
2.  Geben Sie den Namen des Frameworks im Feld **Suchen** ein.  
  
3.  Wählen Sie in der Ergebnisliste das Framework aus, um zur Seite für das Tool in der Visual Studio Gallery zu navigieren.  
  
 So durchsuchen Sie eine Liste der Frameworks und anderer Testtools:  
  
1.  Öffnen Sie [Visual Studio\-Downloads](http://go.microsoft.com/fwlink/?LinkId=236267) auf der MSDN\-Website.  
  
2.  Wählen Sie **Durchsuchen** aus.  
  
3.  Erweitern Sie in der Liste **Kategorie** den Knoten **Tools**, und wählen Sie dann **Test** aus.  
  
4.  Wählen Sie in der Ergebnisliste ein Framework aus, um in Visual Studio Gallery zu der Seite für das Tool zu gelangen.  
  
## Siehe auch  
 [Komponententest für Code](../test/unit-test-your-code.md)
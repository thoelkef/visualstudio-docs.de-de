---
title: "Installieren von Frameworks für Komponententests von Drittanbietern | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c0cd7853c65d5501213076cb7ccb533c5134c9f4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="install-third-party-unit-test-frameworks"></a>Installieren von Frameworks für Komponententests von Drittanbietern
Im Visual Studio-Test-Explorer kann jedes beliebige Framework für Komponententests ausgeführt werden, für den eine Adapterschnittstelle für den Explorer entwickelt wurde. Das Installationsprogramm des Frameworks installiert die Binarys und fügt Visual Studio-Projektvorlagen für die von ihm unterstützten Sprachen hinzu. Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test-Explorer registriert. Eine Visual Studio-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen. Der Test-Explorer kann sie alle ausführen.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>Erwerb von Drittanbieter-Frameworks  
 Sie können viele Komponententest-Frameworks von Drittanbietern oder Visual Studio Marketplace herunterladen und mithilfe des Visual Studio-Erweiterungs-Managers installieren. Frameworks können außerdem von anderen Websites, wie etwa der Website des Frameworks, heruntergeladen werden.  
  
### <a name="installing-from-visual-studio"></a>Installieren in Visual Studio  
  
1.  Wählen Sie im Standardmenü **Tools** und dort **Erweiterungen und Updates** aus.  
  
2.  Erweitern Sie **Online**, **Visual Studio Marketplace**, **Extras**. Wählen Sie **Test** aus.  
  
3.  Suchen Sie das Framework in der Liste.  
  
4.  Wählen Sie das Framework und dann **Herunterladen** aus.  
  
 Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
### <a name="installing-from-the-web"></a>Installation aus dem Web  
 Wenn Sie das Framework kennen, für das Sie sich interessieren:  
  
1.  Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).  
  
2.  Geben Sie den Namen des Frameworks im Feld **Suchen** ein.  
  
3.  Wählen Sie in der Ergebnisliste das Framework aus, um im Visual Studio Marketplace zur Seite für das Tool zu gelangen.  
  
 So durchsuchen Sie eine Liste der Frameworks und anderer Testtools:  
  
1.  Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).  
  
2.  Klicken Sie unter **Nach Kategorie/Sammlung filtern**, auf **Alle anzeigen**.  
  
3.  Erweitern Sie in der Liste **Kategorie** (als **Anzeigen** gekennzeichnet) den Knoten **Extras**, und klicken Sie auf **Testen**.  
  
4.  Wählen Sie in der Ergebnisliste ein Framework aus, um zu einer Visual Studio Marketplace-Seite für das Tool zu gelangen. 

## <a name="update-to-the-latest-test-adapters"></a>Aktualisieren auf die neuesten Testadapter

Aktualisieren Sie auf den neuesten stabilen Testadapter, um eine bessere Testermittlung und Ausführung zu erzielen. Weitere Informationen über Updates für MSTest-, NUnit- und xUnit-Testadapter finden Sie im [Visual Studio-Blog](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>So aktualisieren Sie auf die neueste stabile Testadapterversion

1. Öffnen Sie den NuGet-Paket-Manager für Ihre Projektmappe, indem Sie zu **Extras > NuGet-Paket-Manager > NuGet-Pakete für Projektmappe verwalten...** navigieren.

2. Klicken Sie auf die Registerkarte **Updates**, und suchen Sie nach installierten NUnit- oder xUnit-Testadaptern.

3. Wählen Sie jeden Testadapter und dann im Dropdownmenü die neueste stabile Version aus.

4. Wählen Sie die Schaltfläche **Installieren** aus.

![Aktualisieren des Testadapters](media/installadapter-upgrade.png)

## <a name="see-also"></a>Siehe auch

- [Komponententest für Code](../test/unit-test-your-code.md)

---
title: Installieren von Frameworks für Komponententests von Drittanbietern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660514"
---
# <a name="install-third-party-unit-test-frameworks"></a>Installieren von Frameworks für Komponententests von Drittanbietern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Visual Studio-Test-Explorer kann jedes beliebige Framework für Komponententests ausgeführt werden, für den eine Adapterschnittstelle für den Explorer entwickelt wurde. Das Installationsprogramm des Frameworks installiert die Binarys und fügt Visual Studio-Projektvorlagen für die von ihm unterstützten Sprachen hinzu. Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test-Explorer registriert. Eine Visual Studio-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen. Der Test-Explorer kann sie alle ausführen.

 **Voraussetzungen**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Erwerb von Drittanbieter-Frameworks
 Sie können viele Komponententest-Frameworks von Drittanbietern oder aus der Visual Studio Gallery auf der MSDN-Website herunterladen und mithilfe des Visual Studio-Erweiterungs-Managers installieren. Frameworks können außerdem von anderen Websites, wie etwa der Website des Frameworks, heruntergeladen werden.

### <a name="installing-from-visual-studio"></a>Installieren in Visual Studio

1. Wählen Sie im Standardmenü **Tools** und dort **Erweiterungen und Updates** aus.

2. Erweitern Sie **Online**, **Visual Studio Gallery**, **Tools**. Wählen Sie **Test** aus.

3. Suchen Sie das Framework in der Liste.

4. Wählen Sie das Framework und dann **Herunterladen** aus.

   Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Installation aus dem Web
 Wenn Sie das Framework kennen, für das Sie sich interessieren:

1. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Geben Sie den Namen des Frameworks im Feld **Suchen** ein.

3. Wählen Sie in der Ergebnisliste das Framework aus, um zur Seite für das Tool in der Visual Studio Gallery zu navigieren.

   So durchsuchen Sie eine Liste der Frameworks und anderer Testtools:

4. Öffnen Sie [Visual Studio Marketplace](https://marketplace.visualstudio.com).

5. Wählen Sie **Durchsuchen** aus.

6. Erweitern Sie in der Liste **Kategorie** den Knoten **Tools**, und wählen Sie dann **Test** aus.

7. Wählen Sie in der Ergebnisliste ein Framework aus, um in Visual Studio Gallery zu der Seite für das Tool zu gelangen.

## <a name="see-also"></a>Siehe auch
 [Komponententest für Code](../test/unit-test-your-code.md)

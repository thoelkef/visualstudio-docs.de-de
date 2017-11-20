---
title: 'Vorgehensweise: Lokalisieren einer Funktion | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53dbaa806ae3b65314d5aeed8df9338905a946cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-a-feature"></a>Gewusst wie: Lokalisieren einer Funktion
  Standardmäßig verwenden die Funktionstitel und Beschreibungen hartcodierte Zeichenfolgenwerte. Um den Funktionstitel und die Beschreibung lokalisieren möchten, ersetzen Sie die Zeichenfolgen mit Ausdrücken, die lokalisierte Ressourcen zu verweisen.  
  
## <a name="localizing-a-feature"></a>Lokalisieren einer Funktion  
  
#### <a name="to-localize-a-feature"></a>Zum Lokalisieren einer Funktion  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Feature1** Knoten, und wählen Sie dann **Funktionsressource hinzufügen**.  
  
2.  In der **Ressource hinzufügen** Dialogfeld Wählen Sie **Invariante Sprache** aus der Liste als die Kultur für die Funktionsressourcendatei der Standardsprache.  
  
3.  Wiederholen Sie den vorherigen Schritt für jede lokalisierte Sprache, und wählen die Sprachen Ihrer Wahl für die lokalisierte Funktion Ressourcendateien.  
  
     Separate Funktionsressourcendateien werden erstellt: eine für die Standardsprache und jeweils eine für jede lokalisierte Sprache, die Sie unterstützen möchten.  
  
4.  Öffnen Sie der einzelnen Ressourcendateien im Ressourcen-Editor, und geben Sie dann alle Zeichenfolgen-IDs und ihre Werte.  
  
     Geben Sie beispielsweise in der Standard-Funktionsressourcendatei eine Zeichenfolgen-ID der **Titel** mit einem Wert von **Meine Funktionstitel**, und ein zweites Zeichenfolgen-ID des **Beschreibung** mit einem Wert von **Meine Featurebeschreibung**. Verwenden Sie für jede lokalisierte Ressourcendatei die gleiche Zeichenfolgen-IDs, die in der Standardeinstellung Feature-Ressource verwendet, aber geben Sie lokalisierte Zeichenfolgen für die Werte.  
  
5.  Nachdem Sie alle Werte für die Ressource eingegeben haben, öffnen Sie das Kontextmenü für das Feature (z. B. "Feature1.Feature"), und wählen Sie dann **Sicht-Designer** um die Funktion in der Funktions-Designer zu öffnen.  
  
6.  Zum Lokalisieren der **Titel** und **Beschreibung** Felder in die Funktion mit der Eingabe von Werten in den Feldern im folgenden Format:  
  
     `$Resources:`*Zeichenfolgen-ID*  
  
     Geben Sie z. B. $Resources:**Titel** in der **Funktionstitel** Feld und $Resources:**Beschreibung** in der **Featurebeschreibung** Feld .  
  
     Die Zeichenfolgen-IDs muss denen entsprechen, die in die Ressourcendateien verwendet werden.  
  
7.  Drücken Sie die F5-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
8.  Öffnen Sie in SharePoint die **Websiteaktionen** Menü Wählen Sie **Standorteinstellungen**, und dann auf die **Websiteaktionen** Abschnitt wählen Sie die **Websitefunktionen verwalten** Link.  
  
9. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     Lokalisierte Feature Titel und Beschreibung werden in der Anwendung angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Vorgehensweise: hinzufügen eine Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Vorgehensweise: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)  
  
  
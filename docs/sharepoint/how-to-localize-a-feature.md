---
title: 'Vorgehensweise: Lokalisieren einer Funktion | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f6e796cc00478ee823c345fd02738f8677c36373
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074636"
---
# <a name="how-to-localize-a-feature"></a>Vorgehensweise: Lokalisieren einer Funktion
  Standardmäßig die featuretitel und Beschreibungen, verwenden die hartcodierten Zeichenfolgenwerte. Um den Funktionstitel und die Beschreibung lokalisieren möchten, ersetzen Sie die Zeichenfolgen mit Ausdrücken, die lokalisierte Ressourcen zu verweisen.

## <a name="localize-a-feature"></a>Lokalisieren einer Funktion

#### <a name="to-localize-a-feature"></a>Zum Lokalisieren einer Funktion

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Feature1** Knoten, und wählen Sie dann **Funktionsressource hinzufügen**.

2. In der **Ressource hinzufügen** Dialogfeld wählen **invarianten Sprache** aus der Liste als Kultur für die Funktionsressourcendatei der Standardsprache.

3. Wiederholen Sie den vorherigen Schritt für jede lokalisierte Sprache, und wählen die Sprachen Ihrer Wahl für das lokalisierte Feature Ressourcendateien.

     Separates Feature Ressourcendateien werden erstellt: eine für die Standardsprache und eine für jede lokalisierte Sprache, die Sie unterstützen möchten.

4. Öffnen Sie alle Ressourcen im Ressourcen-Editor, und geben Sie dann die Zeichenfolgen-IDs und ihre Werte.

     Geben Sie beispielsweise in der Standard-Funktionsressourcendatei eine Zeichenfolgen-ID der **Titel** mit einem Wert von **Meine Funktionstitel**, und ein zweites Zeichenfolgen-ID des **Beschreibung** mit einem Wert von **Meine Featurebeschreibung**. Verwenden Sie für jede lokalisierte Ressourcendatei die gleiche Zeichenfolgen-IDs, die in der Standard-Feature-Ressource verwendet allerdings Geben Sie lokalisierte Zeichenfolgen für die Werte ein.

5. Nachdem Sie alle Werte der eingegeben haben, öffnen Sie das Kontextmenü für das Feature (z. B. *"Feature1.Feature"*), und wählen Sie dann **Ansicht-Designer** um das Feature in der Funktions-Designer zu öffnen.

6. Zum Lokalisieren der **Titel** und **Beschreibung** Felder in der Funktion verwenden Sie das folgende Format, Werte in die Felder einzugeben:

     `$Resources:` *Zeichenfolgen-ID*

     Geben Sie beispielsweise die $Resources:**Titel** in die **Funktionstitel** Box und $Resources:**Beschreibung** in die **Featurebeschreibung** Feld .

     Die Zeichenfolgen-IDs muss denen entsprechen, die in den Ressourcendateien verwendet werden.

7. Wählen Sie die **F5** Schlüssel zu erstellen und Ausführen der Anwendung.

8. Öffnen Sie in SharePoint die **Websiteaktionen** Menü wählen **Standorteinstellungen**, und dann auf die **Websiteaktionen** "die Option" der **Websitefunktionen verwalten** Link.

9. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.

     Lokalisierte Feature Titel und Beschreibung werden in der Anwendung angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.

## <a name="see-also"></a>Siehe auch
- [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)
- [Vorgehensweise: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)
- [Vorgehensweise: Lokalisieren von ASPX-markup](../sharepoint/how-to-localize-aspx-markup.md)
- [Vorgehensweise: Lokalisieren von code](../sharepoint/how-to-localize-code.md)

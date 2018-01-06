---
title: Steuerung der Sichtbarkeit eines Symbols oder Decorator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3a4e1927cd17a5cc86ed58565b53f04aeb6977a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuern der Sichtbarkeit eines Symbols oder Decorator-Elements
Ein *Decorator* ist ein Symbol oder eine Textzeile, die auf einer Form in eine domänenspezifische Sprache (DSL) angezeigt wird. Sie können die Decorator-angezeigt und nicht mehr angezeigt, je nach den Status der Eigenschaften im Modell. Auf eine Form, die eine Person darstellt, konnte Sie z. B. unterschiedliche Symbole verfügen, die angezeigt werden, abhängig von der Person Geschlecht, Anzahl der untergeordneten Elemente, und so weiter.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuerung der Sichtbarkeit eines Symbols oder Decorator-Element  
 Das folgende Verfahren wird davon ausgegangen, dass Sie bereits eine Form vom Typ und seine Zuordnung zu einer Domänenklasse definiert haben. Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Um die Sichtbarkeit von ein Symbol oder Text Decorator steuern  
  
1.  In der DSL-Definitionsdiagramm Hinzufügen der Form "-Klasse, die Symbole oder Text Decorator-Elementen, die angezeigt werden sollen.  
  
    1.  Mit der rechten Maustaste der Form "-Klasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf den Typ der Decorator-Element.  
  
    2.  Legen Sie die Decorator **Position** Eigenschaft. Mehr als ein Decorator-Element kann die gleiche Position verfügen. Beispielsweise konnten Sie Symbole für Männlich und Weiblich, die gemeinsame Nutzung der gleichen Position haben.  
  
    3.  Legen Sie die **Symbol "Standard"** ein Symbol Decorator-Eigenschaft.  
  
2.  Wählen Sie die Zuordnung der Diagramm-Element, die der grauen Linie zwischen der Form "-Klasse und die Domänenklasse auf der DSL-Definitionsdiagramm ist.  
  
3.  In der DSL-Detailfenster in die **Decorator-Zuordnungen** Registerkarte, wählen Sie einen Decorator-Element. Beispiel: die MaleDecorator.  
  
4.  Überprüfen Sie die **Sichtbarkeitsfilter** Feld.  
  
5.  Wenn die Eigenschaft "Domain", die Sichtbarkeit zu steuern, sollten auf den unmittelbaren Domänenklasse, lassen **Pfad zur Filter-Eigenschaft** leer.  
  
     Andernfalls klicken Sie auf das Dropdownmenü, und navigieren Sie zu der Beziehung oder eine Klasse, die auf dem sich die Eigenschaft befindet.  
  
    -   Um einen Fehlerbericht zu vermeiden, sollten Sie nicht durch eine Beziehung mit markierten navigieren "*" in der Navigations-Tool.  
  
6.  Legen Sie die **Filtereigenschaft** auf eine Eigenschaft "Domain". Beispielsweise Geschlecht.  
  
7.  In der **Sichtbarkeit Einträge** aufzulisten, fügen Sie die Werte dieser Eigenschaft "Domain" für die die Decorator sichtbar sein sollte. Z. B. Männlich.  
  
8.  Wiederholen Sie die Schritte für jedes Symbol aus.  
  
9. **Transformieren aller Vorlagen**erstellen und auszuführen, und öffnen Sie ein Diagramm.  
  
10. Wenn Sie den steuernden Eigenschaftswert ändern, sollten die Decorator-Elemente angezeigt werden und nicht mehr angezeigt.  
  
 In vielen Fällen möchten Sie die Sichtbarkeit durch eine komplexere Formel als einen einfachen Satz von Werten gesteuert werden. Beispielsweise ist ein Symbol auf der Anzahl der Links eines bestimmten Typs abhängig sind, oder vereinfachen abhängig, ob eine Zahl in einem bestimmten Bereich. In diesem Fall verwenden Sie das folgende Verfahren.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Um die Sichtbarkeit der einen Decorator-Element basierend auf einer Formel zu steuern  
  
1.  Hinzufügen einer berechneten Domäneneigenschaft auf die Domänenklasse. In der **Eigenschaften** Fenster, legen Sie die folgenden Werte:  
  
     **IsBrowsable =**`False`**-wird die Eigenschaft für den Benutzer ausgeblendet**   
  
     **Art =**`Calculated`**– Dies bedeutet, dass Sie Clientcode bereitgestellt werden, die den Wert berechnet.**   
  
     **Namen** z. B. **DecoratorControl**  
  
     **Datentyp** = `Boolean`  
  
     Weitere Informationen finden Sie unter [berechnet und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Stellen Sie die neue Eigenschaft Decorator Sichtbarkeit zu steuern.  
  
    1.  Wählen Sie die Zuordnung der Diagramm-Element, also der grauen Linie von der Domänenklasse mit der Form. In der **DSL-Detailfenster** geöffnete Fenster die **DecoratorMap** Registerkarte.  
  
    2.  Überprüfen Sie die **Sichtbarkeitsfilter** Feld.  
  
    3.  In **Filtereigenschaft**, wählen Sie die Steuerelementeigenschaft **DecoratorControl**.  
  
    4.  Klicken Sie unter **Sichtbarkeit Einträge**, geben Sie `True`.  
  
3.  Klicken Sie auf **alle Vorlagen transformieren** in der Projektmappen-Explorer-Symbolleiste.  
  
4.  Klicken Sie auf **Projektmappe** auf die **erstellen** Menü.  
  
5.  Doppelklicken Sie auf den Fehlerbericht an, die aufgetreten ist: "*YourClass* enthält keine Definition für GetDecoratorControlValue...".  
  
     Auf Dsl\GeneratedCode\DomainClasses.cs wird der Text-Editor geöffnet. Oberhalb der markierten Fehler befindet sich ein Kommentar, der Ihnen das Hinzufügen einer Methode anfordert.  
  
6.  Beachten Sie den Namespace, Klasse und Methode, die fehlen.  Beispielsweise Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  Schreiben Sie eine partielle Klassendefinition, die die fehlende Methode enthält, in einer eigenen Codedatei. Zum Beispiel:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Erstellen Sie neu, und führen Sie die Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)   
 [Festlegen eines Hintergrundbilds in einem Diagramm](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
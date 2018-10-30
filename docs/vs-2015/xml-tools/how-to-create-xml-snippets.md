---
title: 'Vorgehensweise: Erstellen von XML-Ausschnitten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38bec6de97a0b9d38891046a1a6b57f4d31541bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818158"
---
# <a name="how-to-create-xml-snippets"></a>Vorgehensweise: Erstellen von XML-Ausschnitten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Mithilfe des XML-Editors können neue XML-Ausschnitte erstellt werden. Der Editor enthält einen XML-Ausschnitt mit dem Namen "Snippet". Dies ist ein vorformulierter Ausschnitt zum Erstellen neuer XML-Ausschnitte.  
  
## <a name="to-create-a-new-xml-snippet"></a>So erstellen Sie einen neuen XML-Ausschnitt  
 Erstellen Sie einen neuen XML-Code Codeausschnitt erstellen Sie eine neue XML-Datei, und Verwenden der **Ausschnitt einfügen** Feature.  
  
1.  Auf der **Datei** Menü klicken Sie auf **neu** , und klicken Sie dann auf **Datei**.  
  
2.  Klicken Sie auf **XML-Datei** , und klicken Sie dann auf **öffnen**.  
  
3.  Mit der rechten Maustaste im Editor-Bereich, und wählen Sie **Ausschnitt einfügen**.  
  
4.  Wählen Sie **Codeausschnitt** aus der Liste und drücken Sie die EINGABETASTE.  
  
5.  Nehmen Sie die gewünschten Änderungen an dem neuen Ausschnitt vor.  
  
6.  Von der **Datei** Menü die Option **XMLFile.xml speichern**.  
  
     Die **Datei speichern unter** Dialogfeld wird angezeigt.  
  
7.  Geben Sie den Namen für den neuen Ausschnitt aus, und wählen Sie **Codeausschnittsdateien** aus der **Dateityp** Dropdownfenster.  
  
8.  Verwenden der **speichern in** Dropdown-Liste aus, um den Dateispeicherort zu ändern, zu dem Ordner "Eigene Dateien\Visual Studio 2005\Codeausschnitte \XML\My XML Snippets", und drücken dann **speichern**.  
  
## <a name="snippet-description"></a>Ausschnittbeschreibung  
 In diesem Abschnitt werden einige Schlüsselelemente im vorformulierten Ausschnitt beschrieben. Weitere Informationen zu Schema-Elemente, die von der XML-Ausschnitten verwendet, finden Sie unter [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).  
  
### <a name="snippettype-element"></a>SnippetType-Element  
 Vom Editor werden zwei Ausschnitttypen unterstützt:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 Die `Expansion` -Typ bestimmt, ob der Ausschnitt angezeigt, beim Aufrufen wird der **Ausschnitt einfügen** Befehl. Die `SurroundsWith` -Typ bestimmt, ob der Ausschnitt angezeigt, beim Aufrufen wird der **umgeben mit** Befehl.  
  
### <a name="code-element"></a>Codeelement  
 Das `Code`-Element definiert den XML-Text, der beim Aufrufen des Ausschnitts eingefügt wird.  
  
> [!NOTE]
>  Der XML-Ausschnitttext muss in einem `<![CDATA[...]]>`-Abschnitt eingeschlossen werden.  
  
 Es folgt das `Code`-Element, das von einem vorformulierten Ausschnitt erstellt wurde.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 Das `Code`-Element enthält drei Variablen.  
  
- $name$ ist eine benutzerdefinierte Variable. Sie erstellt ein `name`-Element mit einem editierbaren Wert, dessen Standardwert "name" ist. Benutzerdefinierte Variablen werden mithilfe des `Literal`-Elements definiert.  
  
- $selected$ ist eine vordefinierte Variable. Sie stellt den Text dar, der im XML-Editor vor dem Aufrufen des Ausschnitts ausgewählt wurde. Die Positionierung dieser Variablen bestimmt, an welcher Position der ausgewählte Text im Codeausschnitt angezeigt wird, der die Auswahl umgibt.  
  
- $end$ ist eine vordefinierte Variable. Wenn der Benutzer die EINGABETASTE drückt, um die Bearbeitung der Codeausschnittfelder zu beenden, bestimmt diese Variable, an welche Position das Caretzeichen (^) verschoben wird.  
  
  Das obige `Code`-Element fügt den folgenden XML-Text ein:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 Der Wert des name-Elements wird als editierbarer Bereich gekennzeichnet.  
  
### <a name="literal-element"></a>Literalelement  
 Mithilfe des `Literal`-Elements wird der Ersetzungstext angegeben, der nach dem Einfügen in die Datei angepasst werden kann. Literalzeichenfolgen, numerische Werte und einige Variablennamen können beispielsweise als Literale deklariert werden. Sie können in einem XML-Ausschnitt beliebig viele Literale definieren, und Sie können darauf mehrfach aus dem Ausschnitt verweisen. Es folgt ein Beispiel für ein `Literal`-Element, das eine $name$-Variable definiert, deren Standardwert "name" ist.  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Literale können auch auf Funktionen verweisen. Der XML-Editor enthält eine Funktion namens **LookupPrefix**. Die **LookupPrefix** -Funktion sucht den angegebenen Namespace-URI, von der Position in der XML-Dokument, dass dieser Ausschnitt aus aufgerufen wird, und gibt das Namespacepräfix, das für diesen Namespace definiert ist, sofern vorhanden, und fügt den Doppelpunkt (:) In diesem Namen. Folgendes ist ein Beispiel für eine `Literal` -Element, das verwendet die **LookupPrefix** Funktion.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 Die $prefix$-Variable kann anschließend an beliebiger Stelle im XML-Ausschnitt verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Ausschnitte](../xml-tools/xml-snippets.md)   
 [Vorgehensweise: Verwenden von XML-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md)   
 [Gewusst wie: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)




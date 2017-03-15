---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<loc>-JavaScript-XML-Tag"
  - "loc-JavaScript-XML-Tag"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt den Speicherort und den Typ der Sidecardatei an, die lokalisierte IntelliSense\-Informationen bereitstellt.  
  
## Syntax  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### Parameter  
 `filename`  
 Optional.  Der Stammname der Sidecardatei, die Lokalisierungsinformationen für die neutrale Kultur enthält.  Wenn Visual Studio nach Lokalisierungsinformationen sucht, wird versucht, eine kulturspezifische Version dieser Datei zu finden.  Wenn `filename` beispielsweise "jquery.xml" ist, sucht Visual Studio im Speicherort der JS\-Datei, die das `<loc>`\-Element enthält, nach dem richtigen kulturspezifischen Ordner \(wie "JA"\) .  Wenn der kulturspezifische Ordner gefunden wurde, wird überprüft, ob eine Datei "jquery.xml" darin vorhanden ist.  Wenn die richtige Datei nicht gefunden wird, werden stattdessen Speicherortregeln für verwaltete Ressourcen verwendet.  Der Standardwert für `filename` ist der Name der aktuellen Datei, jedoch mit einer XML\-Erweiterung anstelle von JS.  
  
 `format`  
 Optional.  Der Typ der für die Lokalisierung verwendeten Sidecardatei.  Verwenden Sie `messagebundle`, um die Verwendung der von Open Ajax\-Metadaten definierten Meldungsbündel festzulegen.  Das empfohlene Format ist `messagebundle`.  Allerdings wird dieses Format nicht in Microsoft Ajax oder in WINMD\-Dateien unterstützt.  Verwenden Sie `vsdoc`, um das standardmäßige .NET Framework\-Lokalisierungsformat anzugeben, das von Microsoft Ajax und Windows\-Runtime verwendet wird.  Dieses Attribut ist optional.  Das Standardformat ist `vsdoc`.  
  
## Hinweise  
 Das `<loc>`\-Element muss am Dateianfang in demselben Abschnitt wie das `<reference>`\-Element angezeigt werden.  Verwendungsregeln für das `<loc>`\-Element entsprechen denen für das `<reference>`\-Element.  Weitere Informationen finden Sie im Abschnitt "References\-Direktiven" in [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 Visual Studio verarbeitet ein einzelnes `<loc>`\-Element für jede JS\-Datei.  Wenn mehrere `<loc>`\-Elemente vorhanden sind, wird nur ein einzelnes `<loc>`\-Element verwendet.  Verhalten für das Bestimmen, welches zu verwendende `<loc>`\-Element nicht definiert ist.  
  
 Wenn Sie das Meldungsbündelformat verwenden, verwenden Sie das `locid`\-Attribut in XML\-Dokumentationskommentaren, um den `name`\-Attributwert anzugeben.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `<loc>`\-Elements mit dem messagebundle\-Format gezeigt.  Fügen Sie folgenden XML\-Code einer Datei mit dem Namen "messageFilename.xml" hinzu, und speichern Sie die Datei in dem richtigen kulturspezifischen Ordner, wie in der Beschreibung des `filename`\-Parameters angegeben.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Für das messagebundle\-Beispiel fügen Sie den folgenden Code einer JavaScript\-Datei in Ihrem Projekt hinzu.  Das `<loc>`\-Element werden muss als erste Zeile in der JavaScript\-Datei stehen.  Die Beschreibungen in diesem Code werden von lokalisierten Beschreibungen ersetzt, falls verfügbar.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 Im folgenden Beispiel wird das VSDoc\-Format verwendet.  Fügen Sie folgenden XML\-Code einer Datei mit dem Namen "scriptFilename.xml" hinzu, und speichern Sie die Datei im richtigen kulturspezifischen Ordner.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 Für das VSDoc\-Beispiel fügen Sie den folgenden Code einer JavaScript\-Datei in Ihrem Projekt hinzu.  Die Beschreibungen in diesem Code werden von lokalisierten Beschreibungen ersetzt, falls verfügbar.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## Siehe auch  
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)
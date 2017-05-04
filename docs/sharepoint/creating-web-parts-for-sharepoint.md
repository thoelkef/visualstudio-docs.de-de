---
title: "Erstellen von Webparts f&#252;r SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Webparts"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Entwerfen"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Erstellen von Webparts f&#252;r SharePoint
  Unter Verwendung von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint\-Website mithilfe eines Browsers ändern.  Webparts sind serverseitige Steuerelemente, die in einer Webpartseite ausgeführt werden. Diese sind die Bausteine der Seiten, die auf einer SharePoint\-Website angezeigt werden.  Siehe [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Sie können Webparts in einer SharePoint\-Website unter Verwendung von Vorlagen aus Visual Studio erstellen und debuggen.  
  
## Erstellen eines Webparts in Visual Studio  
 Um ein Webpart zu erstellen, fügen Sie jedem SharePoint\-Projekt das Element **Webpart** hinzu.  Sie können ein Element **Webpart** in einer Sandkastenlösung oder einer Farmlösung verwenden.  
  
 Wenn Sie ein Webpart mit einem Designer visuell entwerfen möchten, erstellen Sie ein Projekt vom Typ **Visuelles Webpart**, oder fügen Sie jedem SharePoint\-Projekt ein Element **Visuelles Webpart** hinzu.  Sie können ein Element **Visuelles Webpart** nur in einer Farmlösung verwenden.  
  
### Webpartelement  
 Das Element **Webpart** stellt Dateien bereit, die Sie verwenden können, um ein Webpart für eine SharePoint\-Website zu entwerfen.  Wenn Sie das Element **Webpart** hinzufügen, erstellt Visual Studio einen Ordner im Projekt und fügt diesem Ordner dann mehrere Dateien hinzu.  In der folgenden Tabelle werden die einzelnen Dateien beschrieben.  
  
|Datei|**Beschreibung**|  
|-----------|----------------------|  
|Elements.xml|Enthält Informationen, die von der Funktionsdefinitionsdatei im Projekt verwendet werden, um das Webpart bereitzustellen.|  
|WEBPART\-Datei|Stellt Informationen bereit, die SharePoint benötigt, um das Webpart in einem Webpartkatalog anzuzeigen.|  
|Codedatei|Enthält Methoden, die Steuerelemente zum Webpart hinzufügen und benutzerdefinierten Inhalt innerhalb des Webparts generieren.|  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### Element Visuelles Webpart  
 Ein visuelles Webpart ist ein Webpart, das Sie mit dem Visual Web Developer\-Designer in Visual Studio erstellen.  Siehe [Visual Studio Web Development Content Map](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
 Ein visuelles Webpart funktioniert genauso wie jedes andere Webpart.  Um einem Webpart Steuerelemente wie Schaltflächen und Textfelder hinzuzufügen, fügen Sie einer XML\-Datei Code hinzu.  Einem visuellen Webpart werden Steuerelemente jedoch hinzugefügt, indem sie aus dem **Werkzeugkasten** von Visual Studio in das Webpart gezogen oder kopiert werden.  Der Designer generiert dann den erforderlichen Code in der XML\-Datei.  Siehe [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## SharePoint\-Steuerelemente  
 Visual Studio stellt einige Steuerelemente zum Erstellen von SharePoint\-Seiten \(beispielsweise Anwendungsseiten\) bereit.  Diese Steuerelemente werden im **Werkzeugkasten** unter **SharePoint\-Steuerelemente** angezeigt.  Die Funktionalität dieser Steuerelemente ist von dem [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315)\-Namespace abgeleitet, der ASP.NET\-Serversteuerelemente enthält, die in SharePoint\-Website\- und Listenseiten verwendet werden.  
  
|Steuerelementname|**Beschreibung**|  
|-----------------------|----------------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Fügt ein ASP\-Menü ein.  Weitere Informationen finden Sie unter [Übersicht über das Menü\-Steuerelement](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Fügt ein **LINK**\-Element in der ASPX\-Seite ein und wendet mindestens ein externes Stylesheet an, das von **CssRegistration** definiert wird.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Fügt ein DateTime\-Steuerelement in der ASPX\-Seite ein.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Fügt eine Sicherheitsvalidierung in der ASPX\-Seite ein.|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Gibt eine Eigenschaft einer angegebenen Liste zurück.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Gibt eine globale Eigenschaft der aktuellen Website zurück.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Fügt einen Link zu einem RSS\-Feed in der ASPX\-Seite ein.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Stellt Eigenschaften und Methoden zum Registrieren von Ressourcen \(beispielsweise Skripts\) auf einer Seite bereit, sodass sie angefordert werden können, wenn die Seite gerendert wird.|  
|[Design](http://go.microsoft.com/fwlink/?LinkId=235314)|Wendet ein Design auf die ASPX\-Seite an.|  
  
## Debuggen eines Webparts  
 Sie können ein SharePoint\-Projekt, das ein Webpart enthält, auf dieselbe Weise debuggen wie andere Visual Studio\-Projekte.  Wenn Sie den Visual Studio\-Debugger starten, wird von Visual Studio die SharePoint\-Website geöffnet.  
  
 Um mit dem Debuggen des Codes zu beginnen, fügen Sie das Webpart einer Webpartseite in SharePoint hinzu.  
  
 Weitere Informationen zum Debuggen von SharePoint\-Projekten finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Einschränkungen für visuelle Webparts  
 Ab Visual Studio können Sie visuelle Webparts zu SharePoint\-Sandkastenlösungen und \-Farmlösungen hinzufügen.  Allerdings weisen visuelle Webparts die folgenden Einschränkungen auf:  
  
-   Visuelle Webparts unterstützen keine ersetzbare Parameter.  Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
-   Benutzersteuerelemente oder visuelle Webparts können nicht per Drag&Drop in visuelle Webparts verschoben oder in visuelle Webparts kopiert werden.  Diese Aktion führt zu Buildfehlern.  
  
-   Visuelle Webparts bieten keine direkte Unterstützung von SharePoint\-Servertoken wie $SPUrl.  Weitere Informationen finden Sie in dem Abschnitt zu Einschränkungen von Tokens in visuellen Sandkasten\-Webparts im Thema [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Visuelle Webparts in einer Sandkastenlösung verursachen gelegentlich den Fehler "Die Sandkasten\-Codeausführungsanforderung wurde abgelehnt, weil der Sandkasten\-Codeausführungs\-Hostdienst zu ausgelastet war, um die Anforderung zu verarbeiten." Weitere Informationen zu diesem Fehler finden Sie in diesem im Beitrag im [Blog des SharePoint\-Entwicklerteams](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Serverseitiges JavaScript\-Debugging wird in Visual Studio nicht unterstützt, clientseitiges JavaScript\-Debugging hingegen schon.  
  
     Obwohl Sie einer serverseitigen Markupdatei Inline\-JavaScript hinzufügen können, wird das Debuggen nicht für die dem Markup hinzugefügten Haltepunkte unterstützt.  Um JavaScript zu debuggen, verweisen Sie auf eine externe JavaScript\-Datei in der Markupdatei und legen die Haltepunkte in der JavaScript\-Datei fest.  
  
-   Das Debugging von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Inlinecode muss in der generierten Codedatei statt in der Markupdatei ausgeführt werden.  
  
-   Visuelle Webparts unterstützen die Verwendung der `<@ Assembly Src=`\-Direktive nicht.  
  
-   SharePoint\-Websteuerelemente und einige [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Steuerelemente werden in der SharePoint\-Sandkastenumgebung nicht unterstützt.  Wenn nicht unterstützte Steuerelemente für ein visuelles Webpart in einer Sandkastenlösung verwendet werden, wird der Fehler "Der Typ\- oder Namespacename 'Theme' ist im Namespace 'Microsoft.SharePoint.WebControls' nicht vorhanden" angezeigt.  
  
 Weitere Informationen zu Sandkastenlösungen finden Sie unter [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Erstellen von SharePoint\-basierten Webparts im älteren Format  
 Sie können die Vorlagen in Visual Studio verwenden, um benutzerdefinierte [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]\-Webparts für SharePoint zu erstellen.  [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]\-Webparts werden auf Grundlage der [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Webpartinfrastruktur erstellt und werden als Typ für neue Projekte empfohlen.  
  
 In seltenen Fällen müssen Sie möglicherweise ein Webpart mit dem SharePoint\-basierten Webpart im älteren Format erstellen.  Sie können diese Typen von Webparts mithilfe von Visual Studio erstellen, jedoch stellt Visual Studio keine Vorlagen bereit, die speziell für das Erstellen dieser Webparts ausgelegt sind.  
  
 Weitere Informationen über die Situationen, in denen ein SharePoint\-basiertes Webpart im älteren Format erstellt werden sollte, finden Sie unter [Webpartinfrastruktur in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=169290).  Weitere Informationen zum Erstellen eines SharePoint\-basierten Webparts im älteren Format finden Sie in der [exemplarischen Vorgehensweise zum Erstellen eines grundlegenden SharePoint\-Webparts](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Zeigt das Erstellen von Webparts für SharePoint\-Seiten.|  
|[Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Zeigt das Erstellen von Webparts für SharePoint mithilfe einer visuellen Entwurfsoberfläche.|  
|[Gewusst wie: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|  
|[Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird.|  
|[Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Beschreibt, wie ein Webpart für SharePoint durch Ziehen von Steuerelementen auf eine visuelle Entwurfsoberfläche entworfen wird.|  
|[Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird, das eine Silverlight\-Anwendung hostet und Daten aus SharePoint\-Listen anzeigt.|  
|[Arbeiten mit Visual Web Developer](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Beschreibt die Verwendung des Designers, der angezeigt wird, wenn Sie im Projekt eine Webseite öffnen.|  
  
  
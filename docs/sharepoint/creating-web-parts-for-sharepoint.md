---
title: Erstellen von Webparts für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1efe8524521be590e920818f919a7a52d8fba7e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879133"
---
# <a name="create-web-parts-for-sharepoint"></a>Erstellen von Webparts für SharePoint
  Unter Verwendung von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website mithilfe eines Browsers ändern. Webparts sind serverseitige Steuerelemente, die in einer Webpartseite ausgeführt werden. Diese sind die Bausteine der Seiten, die auf einer SharePoint-Website angezeigt werden. Finden Sie unter [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Sie können Webparts in einer SharePoint-Website unter Verwendung von Vorlagen aus Visual Studio erstellen und debuggen.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Erstellen Sie ein Webpart in Visual Studio
 Erstellen Sie ein Webpart durch Hinzufügen einer **Webpart** Element, das einem SharePoint-Projekt. Sie können eine **Webpart** Element in einer sandkastenlösung oder farmlösung.  
  
 Sollten Sie ein Webpart mit einem Designer visuell zu entwerfen, erstellen Sie eine **visuelles Webpart** oder zum Hinzufügen von **visuelles Webpart** Element, das einem SharePoint-Projekt. Sie können eine **visuelles Webpart** Element in einer farmlösung nur.  
  
### <a name="web-part-item"></a>WebPartElement
 Ein **Webpart** Element enthält Dateien, die Sie verwenden können, um ein Webpart für eine SharePoint-Website zu entwerfen. Beim Hinzufügen einer **Webpart** , Visual Studio erstellt einen Ordner in Ihrem Projekt, und klicken Sie dann den Ordner mehrere Dateien hinzugefügt. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|*"Elements.xml"*|Enthält Informationen, die von der Funktionsdefinitionsdatei im Projekt verwendet werden, um das Webpart bereitzustellen.|  
|WEBPART-Datei|Stellt Informationen bereit, die SharePoint benötigt, um das Webpart in einem Webpartkatalog anzuzeigen.|  
|Codedatei|Enthält Methoden, die Steuerelemente zum Webpart hinzufügen und benutzerdefinierten Inhalt innerhalb des Webparts generieren.|  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Element visuelles Webpart
 Ein visuelles Webpart ist ein Webpart, das Sie mit dem Visual Web Developer-Designer in Visual Studio erstellen. Ein visuelles Webpart funktioniert genauso wie jedes andere Webpart. Um einem Webpart Steuerelemente wie Schaltflächen und Textfelder hinzuzufügen, fügen Sie einer XML-Datei Code hinzu. Aber Sie Steuerelemente hinzufügen eines visuellen Webparts durch Ziehen oder kopieren sie in das Webpart im Visual Studio **Toolbox**. Der Designer generiert dann den erforderlichen Code in der XML-Datei. Weitere Informationen finden Sie unter [How to: Erstellen von SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>SharePoint-Steuerelemente
 Visual Studio stellt einige Steuerelemente zum Erstellen von SharePoint-Seiten (beispielsweise Anwendungsseiten) bereit. Diese Steuerelemente werden in der **Toolbox** unter **SharePoint-Steuerelemente**. Die Funktionalität dieser Steuerelemente leitet sich von der [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) Namespace, der ASP.NET-Serversteuerelemente enthält, die auf SharePoint-Website- und Listenseiten verwendet werden.  
  
|Steuerelementname|Beschreibung|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Fügt ein ASP-Menü ein. Weitere Informationen finden Sie unter [Übersicht über Menu-Steuerelement](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Fügt eine **LINK** Element in der *aspx* Seite und wendet eine oder mehrere externe Stylesheets definiert von **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Fügt ein DateTime-Steuerelement in der *aspx* Seite.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Fügt eine sicherheitsvalidierung in der *aspx* Seite|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Gibt eine Eigenschaft einer angegebenen Liste zurück.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Gibt eine globale Eigenschaft der aktuellen Website zurück.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Fügt einen Link zu einem RSS-feed in die *aspx* Seite.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Stellt Eigenschaften und Methoden zum Registrieren von Ressourcen (beispielsweise Skripts) auf einer Seite bereit, sodass sie angefordert werden können, wenn die Seite gerendert wird.|  
|[Design](http://go.microsoft.com/fwlink/?LinkId=235314)|Wendet ein Design auf die *aspx* Seite.|  
  
## <a name="debug-a-web-part"></a>Debuggen eines Webparts
 Sie können ein SharePoint-Projekt, das ein Webpart enthält, auf dieselbe Weise debuggen wie andere Visual Studio-Projekte. Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.  
  
 Um mit dem Debuggen des Codes zu beginnen, fügen Sie das Webpart einer Webpartseite in SharePoint hinzu.  
  
 Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Visual Webpart-Einschränkungen
 Ab Visual Studio können Sie visuelle Webparts zu SharePoint-Sandkastenlösungen und -Farmlösungen hinzufügen. Allerdings weisen visuelle Webparts die folgenden Einschränkungen auf:  
  
- Visuelle Webparts unterstützen keine ersetzbare Parameter. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
- Benutzersteuerelemente oder visuelle Webparts können nicht per Drag&Drop in visuelle Webparts verschoben oder in visuelle Webparts kopiert werden. Diese Aktion führt zu Buildfehlern.  
  
- Visuelle Webparts bieten keine direkte Unterstützung von SharePoint-Servertoken wie $SPUrl. Weitere Informationen finden Sie unter "Token Einschränkungen in visuellen Sandkasten-Webparts" im Thema [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- Visuelle Webparts in einer Sandkastenlösung verursachen gelegentlich den Fehler "Die Sandkasten-Codeausführungsanforderung wurde abgelehnt, weil der Sandkasten-Codeausführungs-Hostdienst zu ausgelastet war, um die Anforderung zu verarbeiten." Weitere Informationen zu diesem Fehler finden Sie unter diesem Beitrag in der [SharePoint Developer-Teamblog](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- Serverseitiges JavaScript-Debugging wird in Visual Studio nicht unterstützt, clientseitiges JavaScript-Debugging hingegen schon.  
  
   Obwohl Sie einer serverseitigen Markupdatei Inline-JavaScript hinzufügen können, wird das Debuggen nicht für die dem Markup hinzugefügten Haltepunkte unterstützt. Um JavaScript zu debuggen, verweisen Sie auf eine externe JavaScript-Datei in der Markupdatei und legen die Haltepunkte in der JavaScript-Datei fest.  
  
- Das Debugging von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Inlinecode muss in der generierten Codedatei statt in der Markupdatei ausgeführt werden.  
  
- Visuelle Webparts unterstützen die Verwendung der `<@ Assembly Src=`-Anweisung nicht.  
  
- SharePoint-Websteuerelemente und einige [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Steuerelemente werden in der SharePoint-Sandkastenumgebung nicht unterstützt. Wenn nicht unterstützte Steuerelemente für ein visuelles Webpart in einer Sandkastenlösung verwendet werden, wird der Fehler "Der Typ- oder Namespacename 'Theme' ist im Namespace 'Microsoft.SharePoint.WebControls' nicht vorhanden" angezeigt.  
  
  Weitere Informationen zu sandkastenlösungen finden Sie unter [Unterschiede zwischen Sandkasten- und farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Erstellen Sie im älteren Format SharePoint-basierten Webparts.
 Sie können die Vorlagen in Visual Studio verwenden, um benutzerdefinierte [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]-Webparts für SharePoint zu erstellen. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]-Webparts werden auf Grundlage der [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Webpartinfrastruktur erstellt und werden als Typ für neue Projekte empfohlen.  
  
 In seltenen Fällen müssen Sie möglicherweise ein Webpart mit dem SharePoint-basierten Webpart im älteren Format erstellen. Sie können diese Typen von Webparts mithilfe von Visual Studio erstellen, jedoch stellt Visual Studio keine Vorlagen bereit, die speziell für das Erstellen dieser Webparts ausgelegt sind.  
  
 Weitere Informationen, wenn Sie SharePoint-basierten Webparts im älteren Format erstellen möchten, finden Sie unter [Webpartinfrastruktur in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Weitere Informationen dazu, wie Sie ein Webpart zu erstellen, mit der SharePoint-basierten Webparts im älteren Format finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden SharePoint-Webparts](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Zeigt das Erstellen von Webparts für SharePoint-Seiten.|  
|[Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Zeigt das Erstellen von Webparts für SharePoint mithilfe einer visuellen Entwurfsoberfläche.|  
|[Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendung Seite oder eine Webpartseite](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|  
|[Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird.|  
|[Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Beschreibt, wie ein Webpart für SharePoint durch Ziehen von Steuerelementen auf eine visuelle Entwurfsoberfläche entworfen wird.|  
|[Exemplarische Vorgehensweise: Erstellen von Silverlight-Webpart, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Beschreibt, wie ein Webpart für SharePoint entworfen wird, das eine Silverlight-Anwendung hostet und Daten aus SharePoint-Listen anzeigt.|  

---
title: Erweitern von UML-Modellen und-Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 917c88056709cfbeb89ce3f19d9c8da9866feb4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054611"
---
# <a name="extend-uml-models-and-diagrams"></a>Erweitern von UML-Modellen und -Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die verschiedenen Methoden zusammengefasst, mit denen Sie die UML-Modellierungstools von Visual Studio erweitern können. Informationen dazu, welche Versionen von Visual Studio die einzelnen Modelltypen und Tools unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Im folgenden Beispielszenario entwirft und installiert das Unternehmen Fabrikam Gepäckbeförderungssysteme für Flughäfen. Flughafenprojekte weisen viele Ähnlichkeiten auf, was die Grundausrüstung und die Steuersoftware angeht. Allerdings gibt es mehrere Faktoren, die stark variieren können, z. B. die Konfiguration von Fließbändern, Check-in-Schalter, Aufbewahrungsbehälter und andere Ausrüstung für die Gepäckbeförderung.  
  
 Zu Beginn eines neuen Projekts erstellt das Fabrikam-Team ein UML-Modell, das beim Diskutieren dieser Anforderungen im Unternehmen und mit dem Kunden als Unterstützung dient. Aktivitätsdiagramme werden verwendet, um den Gepäckfluss darzustellen, wobei Objektknoten jeweils für Ausrüstungsteile stehen. Das UML-Modell stellt den Code des Systems nicht direkt dar.  
  
 Das Fabrikam-Team für Tools erstellt eine Reihe von Erweiterungen, um die Entwicklungsteams zu unterstützen. In den folgenden Abschnitten werden die verschiedenen Arten von Erweiterungen beschrieben, die Sie definieren können. Sie können mehrere dieser Techniken in einer Visual Studio-Erweiterung kombinieren.  
  
 Weitere Informationen finden Sie in diesem Video: ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo")[MSDN-Reihe: UML-Tools und Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
## <a name="Requirements"></a> Anforderungen  
  
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
- [Modellierungs-SDK für Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profile  
 Mithilfe von Profilen können Sie Stereotype und zusätzliche Eigenschaften für UML-Elemente definieren.  
  
 Die Toolentwickler von Fabrikam definieren Stereotype in den Objektknoten von Aktivitätsdiagrammen, z. B. „Fließband“ und „Check-in-Schalter“. Wenn Teammitglieder mithilfe eines Aktivitätsdiagramms ein Gepäckbeförderungsschema erstellen, können sie jetzt Stereotype festlegen, um anzugeben, welchen Typ der Ausrüstung jeder Knoten darstellt. Die Toolentwickler definieren für einige Stereotype zusätzliche Eigenschaften, sodass Benutzer Werte wie die Kapazität des Fließbands und die Eignung eines Check-in-Schalters aufzeichnen können.  
  
 Weitere Informationen finden Sie unter [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Benutzerdefinierte Toolboxelemente  
 Ein benutzerdefiniertes Toolboxelement erstellt ein Element oder eine Gruppe von Elementen aus einem Prototyp, den Sie in einem Diagramm definieren. Sie können z. B. ein Tool erstellen, das Anwendungsfälle in einer bestimmten Farbe oder mit einem bestimmten Stereotyp erstellt, oder eine Gruppe von Klassen und Zuordnungen, die ein Entwurfsmuster darstellt. Sie können diese Toolboxelemente Visual Studio-Erweiterungen hinzufügen und an andere Benutzer verteilen.  
  
 Weitere Informationen finden Sie unter [Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Validierung  
 Sie können Regeln definieren, um sicherzustellen, dass ein UML-Modell angegebene Einschränkungen erfüllt.  
  
 Die Toolentwickler von Fabrikam definieren Regeln, um Teammitglieder dabei zu unterstützen, einfache Fehler in Bezug auf die Modelle zur Gepäckbeförderung zu vermeiden. Ein Check-in-Schalter kann zum Beispiel nicht direkt mit einem Aufbewahrungsbehälter verbunden sein. Es muss mindestens ein Fließband zwischengeschaltet sein.  
  
 Weitere Informationen finden Sie unter [Definieren von validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Menübefehle  
 Sie können Befehle definieren, die Benutzer aufrufen können, indem sie mit der rechten Maustaste auf Elemente in einem UML-Diagramm klicken. Mit den Befehlen können das Modell und die Diagramme aktualisiert oder andere Vorgänge in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ausgeführt werden.  
  
 Fabrikam definiert Menübefehle, um häufig ausgeführte Vorgänge zu automatisieren, z. B. das Erstellen eines Check-in-Schalters und das Verbinden mit einem bestimmten Fließband oder das Anpassen eines Diagramms an die Layoutregeln des Unternehmens.  
  
 Finden Sie unter [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Gesten  
 Sie können Befehle definieren, die Benutzer per Doppelklick auf ein Diagrammelement oder durch das Ziehen in ein Diagramm oder ein Element des Diagramms initiieren können. Sie können Befehle definieren, die mit Elementen arbeiten können, die aus anderen UML-Diagrammen, anderen Teilen von Visual Studio oder anderen Anwendungen oder Windows-Explorer (oder Datei-Explorer) gezogen werden.  
  
 Mitglieder des Fabrikam-Teams können eine Datei, z. B. eine Spezifikation, jedem Modellelement zuordnen, indem sie diese vom Windows-Desktop ziehen. Die Toolentwickler haben ein Stereotyp definiert, das jedes Element mit einer Dateipfadeigenschaft ausstattet, und eine Geste, die das Stereotyp und den Dateipfad festlegt, wenn eine Datei auf einem Element abgelegt wird.  
  
 Weitere Informationen finden Sie unter [Definieren eines gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Reagieren auf Änderungen  
 Sie können Code schreiben, der auf Änderungen im Modell reagiert, die durch Benutzeraktionen oder anderen Programmcode verursacht wurden.  
  
 Fabrikams Entwickler erstellen Code, in dem die Farbe eines Elements automatisch abhängig von seinem Stereotyp festgelegt wird. Dies erleichtert es den Benutzern, die verschiedenen Rollen der in den Modellen enthaltenen Elemente zu unterscheiden.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Reagieren auf Änderungen in einem UML-Modell](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>ModelBus (Modellbus)  
 Mit einem Modellbus können Sie auf ein Diagramm oder Modell aus einem anderen Diagramm oder einer anderen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterung zugreifen. Unter anderem können Sie Informationen auf diese Weise über mehr als ein Modell verteilen, damit mehrere Personen gleichzeitig am kombinierten Modell arbeiten können.  
  
 Fabrikam verwendet Elemente in Aktivitätsdiagrammen, um Gepäckbeförderungsausrüstung darzustellen. Jedes Element der Ausrüstung kann über eine ausführlichere Spezifikation in einem anderen Diagramm verfügen, das sich in einem anderen Modell befinden kann. Die Validierungseinschränkungen für das Gepäckflussdiagramm können relevante Eigenschaften der Ausrüstung aus den anderen Diagrammen abrufen. Die Verweise auf die anderen Diagramme werden in zusätzlichen Eigenschaften gespeichert, die in Stereotypen definiert sind.  
  
 Weitere Informationen finden Sie unter [Integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Generierung  
 Über ein Modell können Sie Programmcode, Skripts, Konfigurationen, Dokumente, neue Modelle oder andere Artefakte generieren.  
  
 In den Gepäcksystemen, die Fabrikam entwirft, weist der Programmcode von Projekt zu Projekt viele Übereinstimmungen auf. Der Hauptaspekt, der jeweils am stärksten variiert, ist der Plan des Gepäckflusses auf dem jeweiligen Flughafen. Nachdem das Entwurfsteam bei den ersten Projekten Erfahrungen sammeln konnte, erstellen die Toolentwickler eine Vorlage, die über das Gepäckflussmodell einen Großteil des variablen Programmcodes und die anderen Dateien erstellt, z. B. Benutzerdokumente. Die Entwicklungszeit und die Fehlerhäufigkeit kann so für jedes neue Projekt erheblich reduziert werden.  
  
 Weitere Informationen finden Sie unter [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server-Integration  
 Sie können Arbeitselemente mit Modellelementen verknüpfen und programmgesteuert auf die verknüpften Elemente zugreifen.  
  
 Die Toolentwickler von Fabrikam schreiben ein Tool, das für jedes Flughafenprojekt einen Arbeitsplan generiert. Die Arbeitselemente im Zeitplan sind mit den Modellelementen verknüpft.  
  
 Weitere Informationen finden Sie unter [definieren ein linkhandlers für Arbeitsaufgaben](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Tools zur Aktualisierung von Modellen  
 Sie können eigenständige Anwendungen und Visual Studio-Erweiterungen erstellen, die UML-Modelle laden können.  
  
 Die Entwickler von Fabrikam erstellen ein Tool, das ein Modell liest und Berichte über den Fortschritt der Arbeit für jedes Element des Modells generiert.  
  
 Weitere Informationen finden Sie unter [lesen ein UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Domänenspezifische Sprachen  
 Wenn Sie einen bestimmten Modelltyp häufig verwenden, kann es sinnvoll sein, eine domänenspezifische Sprache zu erstellen. Dadurch kann ein UML-Modell genauer auf die Geschäftsanforderungen ausgerichtet werden, die Erstellung und Pflege sind jedoch aufwändiger. Weitere Informationen finden Sie unter [Modellierungs-SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
|**Kategorie**|**Links**|  
|------------------|---------------|  
|**Videos**|![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN-Reihe: UML-Tools und Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML mit Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technische Artikel und Journale**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)   
 [API-Referenz für UML-Modellierungserweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md)

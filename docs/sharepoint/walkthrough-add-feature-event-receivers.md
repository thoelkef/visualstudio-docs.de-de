---
title: "Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern | Microsoft Docs"
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
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e028eb4d95495e92718769979f43012319596960
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-add-feature-event-receivers"></a>Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern
  Funktionsereignisempfänger sind Methoden, die ausgeführt werden, wenn eines der folgenden Feature-bezogene Ereignisse in SharePoint auftritt:  
  
-   Eine Funktion ist installiert.  
  
-   Eine Funktion ist aktiviert.  
  
-   Eine Funktion ist deaktiviert.  
  
-   Eine Funktion wird entfernt.  
  
 Diese exemplarische Vorgehensweise veranschaulicht, wie eine Funktion in einer SharePoint-Projekt einen Ereignisempfänger hinzugefügt wird. Die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen ein leeres Projekt mit einem Funktionsereignisempfänger.  
  
-   Behandlung von der **"FeatureDeactivating"** Methode.  
  
-   Verwenden das Objektmodell der SharePoint-Projekt, um Ankündigungen eine Ankündigung hinzugefügt.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Eine Funktion Ereignisempfängerprojekt erstellen  
 Erstellen Sie zunächst ein Projekt, um den Funktionsereignisempfänger enthalten.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>So erstellen Sie ein Projekt mit eines Funktionsereignisempfängers  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
     Verwenden Sie diesen Projekttyp für Funktionsereignisempfängern, da sie keine Projektvorlage aufweisen.  
  
4.  In der **Namen** Geben Sie **FeatureEvtTest**, und wählen Sie dann die **OK** Schaltfläche zum Anzeigen der **Assistent zum Anpassen von SharePoint**.  
  
5.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite Geben Sie die URL für den SharePoint-Server-Standort, dem Sie das neue benutzerdefinierte Feldelement hinzufügen möchten, oder verwenden den Standardspeicherort (http://\<*System Namen*> /).  
  
6.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld.  
  
     Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die **Fertig stellen** aus, und beachten Sie, dass eine Funktion mit dem Namen Feature1 wird, unter angezeigt der **Funktionen** Knoten.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Die Funktion hinzufügen einen Ereignisempfänger  
 Klicken Sie dann die Funktion fügen Sie einen Ereignisempfänger hinzu, und fügen Sie Code, der ausgeführt wird, wenn die Funktion deaktiviert wird.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Die Funktion einen Ereignisempfänger hinzu  
  
1.  Öffnen Sie das Kontextmenü für den Knoten "Funktionen", und wählen Sie dann **Funktion hinzufügen** beim Erstellen einer Funktion.  
  
2.  Klicken Sie unter der **Funktionen** Knoten, öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignisempfänger hinzufügen** , um die Funktion einen Ereignisempfänger hinzuzufügen.  
  
     Dadurch wird eine Codedatei unter Feature1 hinzugefügt. In diesem Fall heißt es Feature1.EventReceiver.cs oder Feature1.EventReceiver.vb, abhängig von der Entwicklungssprache des Projekts.  
  
3.  Wenn Ihr Projekt, in geschrieben wird [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], fügen Sie den folgenden Code am Anfang des Ereignisempfängers, wenn er noch nicht vorhanden ist:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Die Ereignisempfängerklasse enthält mehrere auskommentierten-Methoden, die als Ereignisse fungieren. Ersetzen Sie die **"FeatureDeactivating"** -Methode durch Folgendes:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Testen des Funktionsereignisempfängers  
 Als Nächstes deaktivieren Sie die Funktion zu testen, ob die **"FeatureDeactivating"** Methode gibt eine Ankündigung SharePoint Ankündigungen.  
  
#### <a name="to-test-the-feature-event-receiver"></a>So testen Sie Funktionsereignisempfängers  
  
1.  Legen Sie den Wert des Projekts auf der **aktive Bereitstellungskonfiguration** Eigenschaft **keine Aktivierung**.  
  
     Durch Festlegen dieser Eigenschaft wird verhindert, dass die Funktion in SharePoint aktiviert und ermöglicht das Debuggen von Funktionsereignisempfängern. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Wählen Sie die **F5** Taste, um das Projekt ausgeführt und in SharePoint bereitzustellen.  
  
3.  Klicken Sie oben auf der SharePoint-Website öffnen die **Websiteaktionen** Menü, und wählen Sie dann **Standorteinstellungen**.  
  
4.  Unter den **Websiteaktionen** Teil der **Standorteinstellungen** Seite der **Websitefunktionen verwalten** Link.  
  
5.  Auf der **Funktionen** Seite, und wählen Sie die **aktivieren** neben der **FeatureEvtTest Feature1** Funktion.  
  
6.  Auf der **Funktionen** Seite, und wählen Sie die **deaktivieren** neben der **FeatureEvtTest Feature1** Funktion, und wählen Sie dann die **Deaktivieren dieser Funktion**  Link zur Bestätigung an die Funktion zu deaktivieren.  
  
7.  Wählen Sie die **Home** Schaltfläche.  
  
     Beachten Sie, die eine Ankündigung wird, in angezeigt der **Ankündigungen** aufzulisten, nachdem die Funktion deaktiviert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  
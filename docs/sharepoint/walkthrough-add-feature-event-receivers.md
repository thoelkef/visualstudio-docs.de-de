---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc22e0c8ae0b0bdaf0729b3cdb3847cd25f580f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008278"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Exemplarische Vorgehensweise: Feature-Ereignisempfänger hinzufügen
  Feature-Ereignisempfänger sind Methoden, die ausgeführt werden, wenn eines der folgenden Feature-bezogene Ereignisse in SharePoint auftritt:

- Ein Feature installiert ist.

- Eine Funktion ist aktiviert.

- Eine Funktion ist deaktiviert.

- Eine Funktion wird entfernt.

  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie einen Ereignisempfänger mit einer Funktion in einer SharePoint-Projekt hinzufügen. Die folgenden Aufgaben veranschaulicht:

- Erstellen ein leeres Projekt mit einem Funktionsereignisempfänger aus.

- Behandeln der **FeatureDeactivating** Methode.

- Verwenden der SharePoint-Projektobjektmodell zum Hinzufügen von einer Ankündigung in die Liste der Ankündigungen

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Eine Funktion Ereignisempfängerprojekt erstellen
 Erstellen Sie zunächst ein Projekt, um den featureereignisempfänger enthält.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Zum Erstellen eines Projekts mit einem Funktionsereignisempfänger

1. Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.

2. Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.

3. In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.

     Verwenden Sie diesen Projekttyp für Feature-Ereignisempfänger, da sie keine Projektvorlage aufweisen.

4. In der **Namen** Geben Sie **FeatureEvtTest**, und wählen Sie dann die **OK** anzuzeigenden Schaltfläche die **SharePoint Customization Wizard**.

5. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL der SharePoint-Website, Server, der Sie das neue Element für benutzerdefiniertes Feld hinzufügen möchten, oder verwenden Sie den Standardspeicherort (http://\<*System Namen*> /).

6. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus.

     Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).

7. Wählen Sie die **Fertig stellen** Schaltfläche, und klicken Sie dann Beachten Sie, dass eine Funktion mit dem Namen Feature1 unter der **Features** Knoten.

## <a name="add-an-event-receiver-to-the-feature"></a>Das Feature einen Ereignisempfänger hinzufügen
 Als Nächstes das Feature fügen Sie einen Ereignisempfänger hinzu, und fügen Sie Code, der ausgeführt wird, wenn die Funktion deaktiviert ist.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Um das Feature einen Ereignisempfänger hinzufügen

1. Öffnen Sie das Kontextmenü für den Knoten "Features", und wählen Sie dann **Feature hinzufügen** um eine Funktion zu erstellen.

2. Unter den **Features** Knoten, öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignisempfänger hinzufügen** das Feature einen Ereignisempfänger hinzu.

     Dadurch wird eine Codedatei unter Feature1 hinzugefügt. In diesem Fall es heißt entweder *Feature1.EventReceiver.cs* oder *Feature1.EventReceiver.vb*, je nach Programmiersprache Ihres Projekts.

3. Wenn Ihr Projekt, im geschrieben wird [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], fügen Sie den folgenden Code am Anfang der Ereignisempfänger, wenn sie nicht bereits vorhanden ist:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. Die Ereignisempfängerklasse enthält mehrere auskommentierte-Methoden, die als Ereignisse fungieren. Ersetzen Sie die **FeatureDeactivating** -Methode durch Folgendes:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Testen Sie den Funktionsereignisempfänger
 Deaktivieren Sie als Nächstes die Funktion zum Testen, ob die **FeatureDeactivating** Methode gibt eine Ankündigung der Ankündigungen für SharePoint-Liste.

#### <a name="to-test-the-feature-event-receiver"></a>So testen Sie den Funktionsereignisempfänger

1. Legen Sie den Wert der Projekt **aktive Bereitstellungskonfiguration** Eigenschaft **keine Aktivierung**.

     Durch Festlegen dieser Eigenschaft wird verhindert, dass die Funktion in SharePoint aktiviert und können Sie das Debuggen von Funktionsereignisempfängern. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

2. Wählen Sie die **F5** Taste, um das Projekt ausführen und in SharePoint bereitzustellen.

3. Öffnen Sie am oberen Rand der Seite für die SharePoint-Webanwendung, die **Websiteaktionen** Menü und wählen Sie dann **Standorteinstellungen**.

4. Unter den **Websiteaktionen** Teil der **Standorteinstellungen** Seite die **Websitefeatures verwalten** Link.

5. Auf der **Features** Seite die **aktivieren** neben der **FeatureEvtTest Feature1** Feature.

6. Auf der **Features** Seite die **deaktivieren** neben der **FeatureEvtTest Feature1** Feature, und wählen Sie dann die **dieses Feature deaktivieren**  Bestätigungslink zum Deaktivieren der Funktion.

7. Wählen Sie die **Startseite** Schaltfläche.

     Eine Ankündigung angezeigt, in der **Ankündigungen** Liste, nachdem die Funktion deaktiviert wird.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
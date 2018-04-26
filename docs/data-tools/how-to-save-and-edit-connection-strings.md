---
title: 'Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a1c0a7bc0659ecee5a65ca254f16eaa2d747ca76
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-save-and-edit-connection-strings"></a>Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen
Verbindungszeichenfolgen in Visual Studio-Anwendungen können in der Anwendungskonfigurationsdatei (auch als Anwendungseinstellungen bezeichnet) gespeichert, oder direkt in der Anwendung fest programmiert werden. Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung. Wenn die Verbindungszeichenfolge geändert werden muss, können Sie das in der Datei mit den Anwendungseinstellungen ändern (und müssen nicht den Quellcode ändern und die Anwendung dann neu kompilieren).

Das Speichern vertraulicher Informationen (z. B. das Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. In der Anwendungskonfigurationsdatei gespeicherte Verbindungszeichenfolgen sind nicht verschlüsselt oder verborgen, sodass es möglich ist, dass jemand auf die Datei zugreift und ihre Inhalte liest. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.

Wenn Sie nicht die integrierte Sicherheit von Windows wählen und die Datenbank einen Benutzernamen und ein Kennwort erfordert, können Sie diese aus der Verbindungszeichenfolge weglassen. Die Anwendung muss diese Informationen aber für eine Verbindung zur Datenbank liefern. Sie können beispielsweise ein Dialogfeld erstellen, dass den Benutzer zur Eingabe dieser Informationen auffordert und dynamisch während der Laufzeit die Verbindungszeichenfolge erstellt. Die Sicherheit kann immer noch ein Problem darstellen, wenn die Informationen auf dem Weg zur Datenbank abgefangen werden.
Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Speichern Sie eine Verbindungszeichenfolge innerhalb des Datenquellen-Konfigurations-Assistenten
In der **Data Source Configuration Wizard**, wählen Sie die Option aus, um die Verbindung auf die Verbindungszeichenfolge speichern zur Seite Anwendungskonfigurationsdatei zu speichern.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>So speichern Sie eine Verbindungszeichenfolge direkt in den Anwendungseinstellungen
- Doppelklicken Sie im Projektmappen-Explorer auf das Symbol "Mein Projekt" (Visual Basic) oder das Symbol "Eigenschaften" (c#), um den Projekt-Designer zu öffnen.
- Wählen Sie die Registerkarte "Einstellungen".
- Geben Sie einen Namen für die Verbindungszeichenfolge ein. Verweisen Sie beim Zugriff auf die Verbindungszeichenfolge im Code auf diesen Namen.
- Legen Sie den Typ (Verbindungszeichenfolge).
- Lassen Sie den Bereich auf Anwendung festgelegt.
- Geben Sie die Verbindungszeichenfolge in das Feld "Wert", oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), im Feld "Wert", öffnen Sie das Dialogfeld Verbindungseigenschaften, um die Verbindungszeichenfolge zu erstellen.

## <a name="editing-connection-strings-stored-in-application-settings"></a>Bearbeiten von Verbindungszeichenfolgen, die in Anwendungseinstellungen gespeichert
Sie können Verbindungsinformationen ändern, die in Anwendungseinstellungen gespeichert ist, mit dem Projekt-Designer.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>So bearbeiten Sie eine Verbindungszeichenfolge, die in den Anwendungseinstellungen gespeichert ist
- Doppelklicken Sie im Projektmappen-Explorer auf das Symbol "Mein Projekt" (Visual Basic) oder das Symbol "Eigenschaften" (c#), um den Projekt-Designer zu öffnen.
- Wählen Sie die Registerkarte "Einstellungen".
- Suchen Sie die Verbindung, die Sie verwenden möchten, bearbeiten, und wählen Sie den Text im Feld "Wert".
- Bearbeiten Sie die Verbindungszeichenfolge im Feld "Wert", oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), in das Feld "Wert" die Verbindung mit dem Dialogfeld Verbindungseigenschaften zu bearbeiten.

## <a name="editing-connection-strings-for-datasets"></a>Bearbeiten von Verbindungszeichenfolgen für datasets
Sie können Verbindungsinformationen für jeden TableAdapter in einem Dataset ändern.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>So bearbeiten eine Verbindungszeichenfolge für einen TableAdapter in einem dataset
- Doppelklicken Sie im Projektmappen-Explorer auf das Dataset (XSD-Datei), die die Verbindung, die Sie bearbeiten möchten.
- Wählen Sie die TableAdapter-Abfrage, die Verbindung aufweist, die Sie bearbeiten möchten.
- Erweitern Sie im Fenster Eigenschaften den Verbindungsknoten aus.
- Um die Verbindungszeichenfolge schnell zu ändern, bearbeiten Sie die ConnectionString-Eigenschaft, oder klicken Sie auf den Pfeil nach unten auf die-Verbindungseigenschaft, und wählen Sie die neue Verbindung.

## <a name="security"></a>Sicherheit
Das Speichern vertraulicher Informationen (z. B. ein Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.
Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Verbindungen](../data-tools/add-new-connections.md)
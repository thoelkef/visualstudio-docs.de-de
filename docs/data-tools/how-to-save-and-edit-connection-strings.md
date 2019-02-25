---
title: 'Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1f8300043f9a16c7d92d72c4dcb22e4cd0432a06
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937551"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen
Verbindungszeichenfolgen in Visual Studio-Anwendungen sind in der Anwendungskonfigurationsdatei (auch als Anwendungseinstellungen bezeichnet) gespeichert, oder direkt in der Anwendung hartcodiert. Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung. Wenn die Verbindungszeichenfolge geändert werden muss, können Sie dies in der Datei mit den Anwendungseinstellungen durchführen (und müssen nicht den Quellcode ändern und die Anwendung dann neu kompilieren).

Das Speichern vertraulicher Informationen (z. B. das Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. In der Anwendungskonfigurationsdatei gespeicherte Verbindungszeichenfolgen sind nicht verschlüsselt oder verschleiert, sodass es möglich ist, dass jemand auf die Datei zugreift und ihre Inhalte liest. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.

Wenn Sie nicht die integrierte Sicherheit von Windows wählen und die Datenbank einen Benutzernamen und ein Kennwort erfordert, können Sie diese aus der Verbindungszeichenfolge weglassen. Die Anwendung muss diese Informationen aber für eine Verbindung zur Datenbank liefern. Sie können beispielsweise ein Dialogfeld erstellen, dass den Benutzer zur Eingabe dieser Informationen auffordert und dynamisch während der Laufzeit die Verbindungszeichenfolge erstellt. Die Sicherheit kann immer noch ein Problem darstellen, wenn die Informationen auf dem Weg zur Datenbank abgefangen werden.
Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Um eine Verbindungszeichenfolge in den Assistenten zur Datenquellenkonfiguration zu speichern.
In der **Assistenten zur Datenquellenkonfiguration**, wählen Sie die Option zum Speichern der Verbindung auf die **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>So speichern Sie eine Verbindungszeichenfolge direkt in den Anwendungseinstellungen
1. Doppelklicken Sie im **Projektmappen-Explorer** auf das Symbol **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), um den **Projekt-Designer** zu öffnen.
1. Wählen Sie die Registerkarte **Einstellungen** aus.
1. Geben Sie einen **Namen** für die Verbindungszeichenfolge ein. Verweisen Sie beim Zugriff auf die Verbindungszeichenfolge im Code auf diesen Namen.
1. Legen Sie den **Typ** auf (**Verbindungszeichenfolge**) fest.
1. Lassen Sie den **Bereich** auf **Anwendung** eingestellt.
1. Geben Sie die Verbindungszeichenfolge in der **Wert** Feld, oder klicken Sie auf die **mit den Auslassungspunkten** Schaltfläche (…), in der **Wert** zu öffnen der **Verbindungseigenschaften** Dialogfeld, um die Verbindungszeichenfolge zu erstellen.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Bearbeiten von Verbindungszeichenfolgen, die in Anwendungseinstellungen gespeichert
Sie können mithilfe des **Projekt-Designers** die Verbindungsinformationen ändern, die in den Anwendungseinstellungen geändert sind.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>So bearbeiten Sie eine Verbindungszeichenfolge, die in den Anwendungseinstellungen gespeichert ist
1. Doppelklicken Sie im **Projektmappen-Explorer** auf das Symbol **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), um den **Projekt-Designer** zu öffnen.
1. Wählen Sie die Registerkarte **Einstellungen** aus.
1. Suchen Sie die Verbindung, die Sie bearbeiten möchten und wählen Sie den Text in die **Wert** Feld.
1. Bearbeiten Sie die Verbindungszeichenfolge in der **Wert** Feld, oder klicken Sie auf die **mit den Auslassungspunkten** Schaltfläche (…), in der **Wert** Feld so bearbeiten Sie die Verbindung mit der **Verbindung Eigenschaften** Dialogfeld.

## <a name="edit-connection-strings-for-datasets"></a>Bearbeiten von Verbindungszeichenfolgen für datasets
Sie können die Verbindungsinformationen für jeden TableAdapter in einem Dataset ändern.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>So bearbeiten Sie eine Verbindungszeichenfolge für einen TableAdapter in einem dataset
1. In **Projektmappen-Explorer**, doppelklicken Sie auf das Dataset (**XSD** Datei), die die zu bearbeitende Verbindung hat.
1. Wählen Sie die **TableAdapter** oder Abfrage, die die Verbindung verfügt, Sie bearbeiten möchten.
1. In der **Eigenschaften** Fenster, erweitern Sie die **Verbindungsknoten**.
1. Um die Verbindungszeichenfolge schnell zu ändern, bearbeiten die **"ConnectionString"** -Eigenschaft, oder klicken Sie auf den Pfeil nach unten auf der **Verbindung** Eigenschaft, und wählen Sie **neue Verbindung**.

## <a name="security"></a>Sicherheit
Das Speichern vertraulicher Informationen (z. B. ein Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.
Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Verbindungen](../data-tools/add-new-connections.md)
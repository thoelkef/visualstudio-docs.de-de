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
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089230"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen
Verbindungszeichenfolgen in Visual Studio-Anwendungen sind in der Anwendungskonfigurationsdatei (auch als Anwendungseinstellungen bezeichnet) gespeichert, oder direkt in der Anwendung hartcodiert. Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung. Wenn die Verbindungszeichenfolge geändert werden muss, können Sie es aktualisieren, in der Datei mit den Anwendungseinstellungen (anstatt sie in den Quellcode ändern und die Anwendung neu kompilieren).

Das Speichern vertraulicher Informationen (z. B. das Kennwort) in der Verbindungszeichenfolge kann sich auf die Sicherheit der Anwendung auswirken. In der Anwendungskonfigurationsdatei gespeicherte Verbindungszeichenfolgen sind nicht verschlüsselt oder verschleiert, sodass es möglich ist, dass jemand auf die Datei zugreift und ihre Inhalte liest. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.

Wenn Sie nicht die integrierte Sicherheit von Windows wählen und die Datenbank einen Benutzernamen und ein Kennwort erfordert, können Sie diese aus der Verbindungszeichenfolge weglassen. Die Anwendung muss diese Informationen aber für eine Verbindung zur Datenbank liefern. Sie können beispielsweise ein Dialogfeld erstellen, dass den Benutzer zur Eingabe dieser Informationen auffordert und dynamisch während der Laufzeit die Verbindungszeichenfolge erstellt. Die Sicherheit kann immer noch ein Problem darstellen, wenn die Informationen auf dem Weg zur Datenbank abgefangen werden.
Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Um eine Verbindungszeichenfolge in den Assistenten zur Datenquellenkonfiguration zu speichern.
In der **Assistenten zur Datenquellenkonfiguration**, wählen Sie die Option zum Speichern der Verbindung auf die **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>So speichern Sie eine Verbindungszeichenfolge direkt in den Anwendungseinstellungen
1. In **Projektmappen-Explorer**, doppelklicken Sie auf die **Mein Projekt** Symbol (Visual Basic) oder **Eigenschaften** (c#), zum Öffnen der **Projekt-Designer** .
1. Wählen Sie die **Einstellungen** Registerkarte.
1. Geben Sie einen **Namen** für die Verbindungszeichenfolge. Verweisen Sie beim Zugriff auf die Verbindungszeichenfolge im Code auf diesen Namen.
1. Legen Sie die **Typ** auf (**Verbindungszeichenfolge**).
1. Lassen Sie die **Bereich** festgelegt **Anwendung**.
1. Geben Sie die Verbindungszeichenfolge in der **Wert** Feld, oder klicken Sie auf die **mit den Auslassungspunkten** Schaltfläche (…), in der **Wert** zu öffnen der **Verbindungseigenschaften** Dialogfeld, um die Verbindungszeichenfolge zu erstellen.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Bearbeiten von Verbindungszeichenfolgen, die in Anwendungseinstellungen gespeichert
Sie können die Verbindungsinformationen, die in den Anwendungseinstellungen, mithilfe gespeichert wird der **Projekt-Designer**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>So bearbeiten Sie eine Verbindungszeichenfolge, die in den Anwendungseinstellungen gespeichert ist
1. In **Projektmappen-Explorer**, doppelklicken Sie auf die **Mein Projekt** Symbol (Visual Basic) oder **Eigenschaften** (c#), zum Öffnen der **Projekt-Designer** .
1. Wählen Sie die **Einstellungen** Registerkarte.
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
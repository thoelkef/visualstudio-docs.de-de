---
title: Erweiterte Sicherheitseinstellungen (Dialogfeld)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fec353f6ede2a9d2f99a8dfc19611577bbc6160
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="advanced-security-settings-dialog-box"></a>Erweiterte Sicherheitseinstellungen (Dialogfeld)
Mit diesem Dialogfeld können Sie Sicherheitseinstellungen bezüglich des Debuggens in einer Zone angeben.

 Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**. Wählen Sie auf der Seite **Sicherheit** die Option **ClickOnce-Sicherheitseinstellungen aktivieren** aus, klicken Sie auf **Teilweise vertrauenswürdige Anwendung**, und klicken Sie dann auf **Erweitert**.

## <a name="uielement-list"></a>UIElement-Liste
 **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen:** Wenn Sie dieses Kontrollkästchen aktivieren, wird der auf der Seite **Sicherheit** ausgewählte Berechtigungssatz während des Debuggens verwendet. Diese Option ist standardmäßig ausgewählt.

 Diese Option muss aktiviert sein, damit das Debuggen in einer Sicherheitszone funktioniert. Die Option **Visual Studio-Hostprozess aktivieren** (auf der Seite **Debuggen** des **Projekt-Designers** verfügbar) muss ebenso aktiviert sein.

 Für Projekte der WPF-Webbrowseranwendung ist die Option **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen** ausgewählt und deaktiviert.

 **Der Anwendung Zugriff auf die Ursprungssite gewähren:** Wenn Sie dieses Kontrollkästchen aktivieren, kann die Anwendung auf die Website oder die Serverfreigabe, auf der sie veröffentlicht wird, zugreifen. Diese Option ist standardmäßig ausgewählt.

 **Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde:** Wenn Sie der Anwendung gestatten müssen, auf die Website oder die Serverfreigabe entsprechend der **Installations-URL** zuzugreifen, die Sie auf der Seite **Veröffentlichen** angegeben haben, geben Sie die URL hier ein. Diese Option ist nur verfügbar, wenn **Der Anwendung Zugriff auf die Ursprungssite gewähren** ausgewählt ist.

## <a name="see-also"></a>Siehe auch

- [Seite „Sicherheit“, Projekt-Designer](../../ide/reference/security-page-project-designer.md)
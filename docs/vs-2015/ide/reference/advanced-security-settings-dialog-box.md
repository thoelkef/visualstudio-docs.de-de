---
title: Erweiterte Sicherheitseinstellungen (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651741"
---
# <a name="advanced-security-settings-dialog-box"></a>Erweiterte Sicherheitseinstellungen (Dialogfeld)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit diesem Dialogfeld können Sie Sicherheitseinstellungen bezüglich des Debuggens in einer Zone angeben.

 Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Wenn der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit** . Aktivieren Sie auf der Seite **Sicherheit** die Option **ClickOnce-Sicherheitseinstellungen aktivieren**, klicken Sie auf **diese Anwendung ist eine teilweise vertrauenswürdige Anwendung**, und klicken Sie dann auf **erweitert**.

## <a name="uielement-list"></a>UIElement-Liste
 **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen:** Wenn Sie dieses Kontrollkästchen aktivieren, wird der auf der Seite **Sicherheit** ausgewählte Berechtigungssatz während des Debuggens verwendet. Diese Option ist standardmäßig ausgewählt.

 Diese Option muss aktiviert sein, damit das Debuggen in einer Sicherheitszone funktioniert. Die Option **Visual Studio-Hostprozess aktivieren** (auf der Seite **Debuggen** des **Projekt-Designers** verfügbar) muss ebenso aktiviert sein.

 Für Projekte der WPF-Webbrowseranwendung ist die Option **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen** ausgewählt und deaktiviert.

 **Der Anwendung Zugriff auf die Ursprungssite gewähren:** Wenn Sie dieses Kontrollkästchen aktivieren, kann die Anwendung auf die Website oder die Serverfreigabe, auf der sie veröffentlicht wird, zugreifen. Diese Option ist standardmäßig ausgewählt.

 **Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde:** Wenn Sie der Anwendung gestatten müssen, auf die Website oder die Serverfreigabe entsprechend der **Installations-URL** zuzugreifen, die Sie auf der Seite **Veröffentlichen** angegeben haben, geben Sie die URL hier ein. Diese Option ist nur verfügbar, wenn **Der Anwendung Zugriff auf die Ursprungssite gewähren** ausgewählt ist.

## <a name="see-also"></a>Weitere Informationen
 [Seite "Sicherheit", Projekt-Designer](../../ide/reference/security-page-project-designer.md)

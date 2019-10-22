---
title: Überprüfen des UML-Modells | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659371"
---
# <a name="validate-your-uml-model"></a>Überprüfen des UML-Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einige der UML-Modelle, die Sie in Visual Studio zeichnen können, werden in Ihrem Projekt möglicherweise als ungültig betrachtet. So kann es beispielsweise erforderlich sein, dass ein Anwendungsfall immer mit einem Sequenzdiagramm verknüpft ist, das über Lebenslinien verfügt, die die Akteure des Anwendungsfalls darstellen. Sie können *Einschränkungen* installieren oder definieren, die Ihrem Team bei der Einhaltung von Anforderungen wie diesem helfen. Einschränkungen können angewendet werden, wenn der Benutzer ein Modell speichert oder öffnet, und können über einen Menübefehl aufgerufen werden.

 In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] werden keine Einschränkungen bereitgestellt, da sie davon abhängen, auf welche Weise UML-Modelle von Ihrem Team interpretiert und genutzt werden. Sie können jedoch eigene Einschränkungen definieren und von anderen Benutzern definierte Einschränkungen installieren. Weitere Informationen zum Definieren von Einschränkungen und zum Packen dieser Einschränkungen für die Verteilung finden Sie unter [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Aufrufen der Validierung
 Wenn Sie eine Validierungserweiterung installiert haben, können die darin bereitgestellten Einschränkungen in den folgenden Fällen angewendet werden. Einige Einschränkungen können nicht in allen der folgenden Fälle angewendet werden.

- **Überprüfungs Befehl.** Um die Validierung jederzeit aufzurufen, klicken Sie im Menü **Architektur** auf **UML-Modell** überprüfen.

  > [!NOTE]
  > Der Befehl wird nur angezeigt, wenn Validierungseinschränkungen installiert sind.

- **Beim Speichern eines Modells.** Validierungseinschränkungen können beim Speichern des Modells angewendet werden. Mithilfe dieser Einschränkungen soll sichergestellt werden, dass Sie kein Modell speichern, das gemäß der Interpretation durch das Projekt ungültig ist.

   Falls Fehler auftreten, werden Sie gefragt, ob Sie das Modell trotzdem speichern möchten. Sie können entweder die Fehler korrigieren oder das Modell dennoch speichern.

- **Beim Öffnen eines Modells.** Wenn Sie ein Modell öffnen, können Validierungsmethoden angewendet werden, um Fehlermeldungen wiederherzustellen, die beim Speichern des Modells vorhanden waren. Fehler können auch aufgrund von Inkonsistenzen zwischen den Änderungen von Benutzern auftreten, die an verschiedenen Teilen eines Modells arbeiten. Weitere Informationen finden Sie unter [Freigeben von Modellen und Exportieren von Diagrammen](../modeling/share-models-and-exporting-diagrams.md).

  Validierungsfehler werden im Fehlerfenster von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gemeldet.

  Doppelklicken Sie auf einen Fehler, um die fehlerhaften Elemente in einem Diagramm auszuwählen. Dies funktioniert nur, wenn die fehlerhaften Elemente in einem geöffneten Diagramm sichtbar sind.

## <a name="installing-validation-constraints"></a>Installieren von Validierungseinschränkungen
 Einschränkungen sind in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterungsdateien (VSIX-Dateien) gepackt. In der Regel ist ein Satz Einschränkungen Teil einer Erweiterung, die auch andere Definitionen wie Menübefehle, Profile und Toolboxelemente enthält.

#### <a name="to-install-a-visual-studio-extension"></a>So installieren Sie eine Visual Studio-Erweiterung

1. Doppelklicken Sie im Windows-Explorer (oder Datei-Explorer) auf die **VSIX** -Datei.

2. Starten Sie eine beliebige bereits ausgeführte Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] neu.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Deaktivieren und Deinstallieren von Validierungseinschränkungen
 Wenn Sie mit einem Modell arbeiten möchten, für das die Einschränkungen nicht gelten, können Sie die Erweiterung mit den Einschränkungen vorübergehend deaktivieren. Dank der Möglichkeit zum Aktivieren und Deaktivieren verschiedener Erweiterungen können Sie zu unterschiedlichen Zeiten an unterschiedlichen Arten von Modellen arbeiten.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>So deaktivieren oder deinstallieren Sie eine Visual Studio-Erweiterung

1. Klicken Sie im **Menü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]** Extras auf **Erweiterungen und Updates**.

2. Klicken Sie neben der Erweiterung auf **Deaktivieren** , um die Erweiterung vorübergehend zu deaktivieren. Sie können Sie später erneut aktivieren, indem Sie zum Fenster **Erweiterungen und Updates** zurückkehren.

     \- oder -

     Klicken Sie auf **deinstallieren** , um die Erweiterung zu entfernen.

3. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]neu.

## <a name="see-also"></a>Siehe auch
 [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md) [Erstellen von Modellen für Ihre APP verwenden von](../modeling/create-models-for-your-app.md) [Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

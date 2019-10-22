---
title: Metadaten als Quelle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b1d96224be13a12dcaadb394584f8441c7bd1934
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667514"
---
# <a name="metadata-as-source"></a>Metadaten als Quelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Metadaten als Quelle können Sie Metadaten anzeigen, die als C#-Quellcode in einem schreibgeschützten Puffer auftreten. Dies ermöglicht eine Ansicht der Deklarationen von Typen und Membern (ohne Implementierungen). Sie können Metadaten als Quelle anzeigen, indem Sie den Befehl **Gehe zu Definition** für Typen oder Member ausführen, deren Quellcode nicht in Ihrem Projekt oder Ihrer Projektmappe verfügbar ist.

> [!NOTE]
> Wenn Sie versuchen, den **Gehe zu Definition** -Befehl für Typen oder Member auszuführen, die als intern gekennzeichnet sind, zeigt die IDE (integrierte Entwicklungsumgebung) ihre Metadaten nicht als Quelle an, unabhängig davon, ob die referenzierende Assembly ein Friend ist oder nicht.

 Sie können Metadaten als Quelle entweder im Code-Editor oder im **Codedefinitionsfenster** anzeigen.

## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Anzeigen von Metadaten als Quelle im Code-Editor
 Wenn Sie den Befehl **Gehe zu Definition** für ein Element ausführen, dessen Quellcode nicht verfügbar ist, wird ein Dokument mit Registerkarten im Code-Editor angezeigt, das eine Ansicht der Metadaten des betreffenden Elements in der Darstellung als Quelle enthält. Der Name des Typs wird auf der Registerkarte des Dokuments angezeigt, gefolgt von **[aus Metadaten]** .

 Wenn Sie beispielsweise den Befehl **Gehe zu Definition** für <xref:System.Console>ausführen, werden Metadaten für <xref:System.Console> im Code-Editor als C#-Quellcode angezeigt, die seiner Deklaration ähnlich sehen, jedoch ohne Implementierung.

 ![Metadaten als Quelle](../csharp-ide/media/metadatasource.png "MetadataSource")

## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Anzeigen von Metadaten als Quelle im Codedefinitionsfenster
 Wenn das **Codedefinitionsfenster** aktiv oder sichtbar ist, führt die IDE automatisch den Befehl **Gehe zu Definition** für Elemente unter dem Cursor im Code-Editor sowie für Elemente aus, die in der **Klassenansicht** oder im **Objekt-Browser**ausgewählt sind. Wenn der Quellcode für das betreffende Element nicht verfügbar ist, zeigt die IDE die Metadaten des betreffenden Elements als Quelle im **Codedefinitionsfenster** an.

 Wenn Sie beispielsweise Ihren Cursor innerhalb des Worts <xref:System.Console> im Code-Editor platzieren, werden Metadaten für <xref:System.Console> als Quelle im **Codedefinitionsfenster** angezeigt. Die Quelle ähnelt der <xref:System.Console> -Deklaration, jedoch ohne Implementierung.

 Wenn Sie die Deklaration eines Elements sehen möchten, das im **Codedefinitionsfenster** angezeigt wird, klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie dann auf **Gehe zu Definition**.
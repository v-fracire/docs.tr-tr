---
title: Sistem Bilgileri ve Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: 727bcc53750081ae2d957527332ed3199c7d8e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524121"
---
# <a name="system-information-and-windows-forms"></a>Sistem Bilgileri ve Windows Forms
Bazen, uygulama kodunuzda kararları için üzerinde çalıştığı bilgisayar hakkında bilgi toplamak gereklidir. Örneğin, yalnızca belirli bir ağ etki alanına bağlı olduğunda geçerlidir bir işleve sahip olabilir; Bu durumda etki alanını belirlemek ve etki alanı mevcut değilse işlevi devre dışı bırakmak için bir yol gerekir.  
  
 Windows Forms uygulamaları kullanabileceğiniz <xref:System.Windows.Forms.SystemInformation> çalışma zamanında bir bilgisayar ile ilgili birkaç belirlemek için sınıf. Aşağıdaki örnek, kullanma gösterir <xref:System.Windows.Forms.SystemInformation> almak için sınıf <xref:System.Windows.Forms.SystemInformation.UserName%2A> ve <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 Tüm üyeleri <xref:System.Windows.Forms.SystemInformation> sınıfı salt okunur; kullanıcının ayarlarını değiştiremezsiniz. Sınıfı, 100'den üyeleri bilgi her şeyi bilgisayara bağlı monitör sayısını döndürme vardır (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) için Windows Gezgini'nde simgeler aralığını (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> ve <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Bazı daha kullanışlı üyelerinin <xref:System.Windows.Forms.SystemInformation> sınıfı dahil <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, ve <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SystemInformation>  
 [Windows Forms'ta Güç Yönetimi](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)

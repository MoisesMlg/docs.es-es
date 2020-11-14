---
title: Serialización binaria
description: En este artículo se describe la serialización binaria y los tipos para los que .NET Core la admite. Tenga en cuenta los peligros de la serialización binaria y sus alternativas.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: bfb504862232345db07bdc92993069fc87afdbeb
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282096"
---
# <a name="binary-serialization"></a>Serialización binaria

La serialización se puede definir como el proceso de almacenar el estado de un objeto a los medios de almacenamiento. Durante este proceso, los campos públicos y privados del objeto y el nombre de la clase, incluso el ensamblado que contiene la clase, se convierten en una secuencia de bytes, que se escribe a continuación en un flujo de datos. Cuando se deserializa el objeto como consecuencia, se crea un clon exacto del objeto original.

Al implementar un mecanismo de la serialización en un entorno orientado a objetos, tiene que realizar varios intercambios entre la facilidad de uso y la flexibilidad. El proceso se puede automatizar en gran medida, con tal de que sea proporcionado el control suficiente sobre el proceso. Por ejemplo, las situaciones se pueden presentar donde la serialización binaria simple no es suficiente, o podría haber una razón concreta para decidir qué campos en una clase necesitan ser serializados. Las secciones siguientes examinan el sólido mecanismo de serialización proporcionado con .NET y resaltan varias características importantes que permiten personalizar el proceso para satisfacer las necesidades.

> [!NOTE]
> El estado de un objeto UTF-8 o UTF-7 codificado no se conserva si el objeto se serializa y se deserializa utilizando distintas versiones de .NET.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

La serialización binaria permite modificar miembros privados dentro de un objeto y, por tanto, cambiar su estado. Por este motivo, se recomiendan otros marcos de serialización, como <xref:System.Text.Json?displayProperty=fullName>, que operan en la superficie de la API pública.

## <a name="net-core"></a>.NET Core

.NET Core admite la serialización binaria para un subconjunto de tipos. Puede ver la lista de tipos compatibles en la sección [Tipos serializables](#serializable-types) siguiente. Se garantiza que los tipos indicados son serializables entre .NET Framework 4.5.1 y versiones posteriores, y entre .NET Core 2.0 y versiones posteriores. Otras implementaciones de .NET, como Mono, no son oficialmente compatibles, pero también deberían funcionar.

### <a name="serializable-types"></a>Tipos serializables

> [!div class="mx-tdCol2BreakAll"]
> | Tipo | Notas |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.AggregateException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4.<br/>No se admite la serialización desde .NET Framework a .NET Core. |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DBNull?displayProperty=nameWithType> | A partir de .NET Core 2.0.2 y versiones posteriores. |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | Si establece `RemotingFormat` en `SerializationFormat.Binary`, solo se puede intercambiar con .NET Core 2.1 y versiones posteriores. |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4.<br/>No se admite la serialización desde .NET Framework a .NET Core |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | A partir de .NET Core 2.0.4. |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | A partir de .NET Core 2.0.6. |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.FormatException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.OverflowException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.RankException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4.<br/>No se admite la serialización desde .NET Framework a .NET Core. |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4.<br/>Datos de serialización limitados. |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | No es serializable en .NET Framework 4.7 y versiones anteriores. |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | A partir de .NET Core 2.0.4. |

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.Serialization>\
Contiene clases que se pueden usar para serializar y deserializar objetos.

- [Serialización SOAP y XML](xml-and-soap-serialization.md)\
Describe el mecanismo de la serialización XML que está incluido con Common Language Runtime.

- [Seguridad y serialización](../../framework/misc/security-and-serialization.md)\
Describe las instrucciones de la codificación seguras que hay que seguir al escribir el código que realiza la serialización.

- [Comunicación remota de .NET](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
Describe los diversos métodos en .NET Framework para las comunicaciones remotas.

- [Servicios web XML creados con ASP.NET y clientes de servicio web XML](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
Artículos en los que se describe y explica cómo programar servicios web XML creados con ASP.NET.

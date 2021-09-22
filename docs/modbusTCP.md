# ModbusTCP

## ModbusTCP.Master

Modbus TCP common driver class.

This class implements a modbus TCP master driver. It supports the following commands: Read coils Read discrete inputs Write single coil Write multiple cooils Read holding register Read input register Write single register Write multiple register All commands can be sent in synchronous or asynchronous mode. If a value is accessed in synchronous mode the program will stop and wait for slave to response. If the slave didn't answer within a specified time a timeout exception is called. The class uses multi threading for both synchronous and asynchronous access. For the communication two lines are created. This is necessary because the synchronous thread has to wait for a previous command to finish. The synchronous channel can be disabled during connection. This can be necessary when the slave only supports one connection.

## Constants

`ModbusTCP.Master.excIllegalFunction`

Constant for exception illegal function.

---

`ModbusTCP.Master.excIllegalDataAdr`

Constant for exception illegal data address.

---

`ModbusTCP.Master.excIllegalDataVal`

Constant for exception illegal data value.

---

`ModbusTCP.Master.excSlaveDeviceFailure`

Constant for exception slave device failure.

---

`ModbusTCP.Master.excAck`

Constant for exception acknowledge. This is triggered if a write request is executed while the watchdog has expired.

---

`ModbusTCP.Master.excSlaveIsBusy`

Constant for exception slave is busy/booting up.

---

`ModbusTCP.Master.excGatePathUnavailable`

Constant for exception gate path unavailable.

---

`ModbusTCP.Master.excExceptionNotConnected`

Constant for exception not connected.

---

`ModbusTCP.Master.excExceptionConnectionLost`

Constant for exception connection lost.

---

`ModbusTCP.Master.excExceptionTimeout`

Constant for exception response timeout.

---

`ModbusTCP.Master.excExceptionOffset`

Constant for exception wrong offset.

---

`ModbusTCP.Master.excSendFailt`

Constant for exception send failt.

## Events

`ModbusTCP.Master.ResponseData`

Response data event. This event is called when new data arrives

---

`ModbusTCP.Master.OnResponseData`

Response data event. This event is called when new data arrives

---

`ModbusTCP.Master.ExceptionData`

Exception data event. This event is called when the data is incorrect

---

`ModbusTCP.Master.OnException`

Exception data event. This event is called when the data is incorrect

## Properties

`ModbusTCP.Master.timeout`

Response timeout. If the slave didn't answers within in this time an exception is called.

Value: The default value is 500ms.

---

`ModbusTCP.Master.refresh`

Refresh timer for slave answer. The class is polling for answer every X ms.

Value: The default value is 10ms.

---

`ModbusTCP.Master.NoSyncConnection`

Displays the state of the synchronous channel

Value: True if channel was diabled during connection.

---

`ModbusTCP.Master.connected`

Shows if a connection is active.

## Methods

`ModbusTCP.Master()`

Create master instance without parameters.

---

`ModbusTCP.Master(System.String,System.UInt16)`

Create master instance with parameters.

| Name  | Description                                            |
| ----- | ------------------------------------------------------ |
| ip:   | IP adress of modbus slave.                             |
| Name  | Description                                            |
| ----- | ------                                                 |
| port: | Port number of modbus slave. Usually port 502 is used. |

---

`ModbusTCP.Master(System.String,System.UInt16,System.Boolean)`

Create master instance with parameters.

| Name                | Description                                            |
| ------------------- | ------------------------------------------------------ |
| ip:                 | IP adress of modbus slave.                             |
| Name                | Description                                            |
| -----               | ------                                                 |
| port:               | Port number of modbus slave. Usually port 502 is used. |
| Name                | Description                                            |
| -----               | ------                                                 |
| no_sync_connection: | Disable second connection for synchronous requests     |

---

`ModbusTCP.Master.connect(System.String,System.UInt16,System.Boolean)`

Start connection to slave.

| Name                | Description                                            |
| ------------------- | ------------------------------------------------------ |
| ip:                 | IP adress of modbus slave.                             |
| Name                | Description                                            |
| -----               | ------                                                 |
| port:               | Port number of modbus slave. Usually port 502 is used. |
| Name                | Description                                            |
| -----               | ------                                                 |
| no_sync_connection: | Disable sencond connection for synchronous requests    |

---

`ModbusTCP.Master.disconnect()`

Stop connection to slave.

---

`ModbusTCP.Master.Finalize()`

Destroy master instance.

---

`ModbusTCP.Master.Dispose()`

Destroy master instance

---

`ModbusTCP.Master.ReadCoils(System.UInt16,System.Byte,System.UInt16,System.UInt16)`

Read coils from slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |

---

`ModbusTCP.Master.ReadCoils(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[])`

Read coils from slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the result of function.                                                                             |

---

`ModbusTCP.Master.ReadDiscreteInputs(System.UInt16,System.Byte,System.UInt16,System.UInt16)`

Read discrete inputs from slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |

---

`ModbusTCP.Master.ReadDiscreteInputs(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[])`

Read discrete inputs from slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the result of function.                                                                             |

---

`ModbusTCP.Master.ReadHoldingRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16)`

Read holding registers from slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |

---

`ModbusTCP.Master.ReadHoldingRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[])`

Read holding registers from slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the result of function.                                                                             |

---

`ModbusTCP.Master.ReadInputRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16)`

Read input registers from slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |

---

`ModbusTCP.Master.ReadInputRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[])`

Read input registers from slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numInputs:    | Length of data.                                                                                              |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the result of function.                                                                             |

---

`ModbusTCP.Master.WriteSingleCoils(System.UInt16,System.Byte,System.UInt16,System.Boolean)`

Write single coil in slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| OnOff:        | Specifys if the coil should be switched on or off.                                                           |

---

`ModbusTCP.Master.WriteSingleCoils(System.UInt16,System.Byte,System.UInt16,System.Boolean,System.Byte[])`

Write single coil in slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| OnOff:        | Specifys if the coil should be switched on or off.                                                           |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| result:       | Contains the result of the synchronous write.                                                                |

---

`ModbusTCP.Master.WriteMultipleCoils(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[])`

Write multiple coils in slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numBits:      | Specifys number of bits.                                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the bit information in byte format.                                                                 |

---

`ModbusTCP.Master.WriteMultipleCoils(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.Byte[],System.Byte[])`

Write multiple coils in slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address from where the data read begins.                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| numBits:      | Specifys number of bits.                                                                                     |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the bit information in byte format.                                                                 |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| result:       | Contains the result of the synchronous write.                                                                |

---

`ModbusTCP.Master.WriteSingleRegister(System.UInt16,System.Byte,System.UInt16,System.Byte[])`

Write single register in slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address to where the data is written.                                                                        |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the register information.                                                                           |

---

`ModbusTCP.Master.WriteSingleRegister(System.UInt16,System.Byte,System.UInt16,System.Byte[],System.Byte[])`

Write single register in slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address to where the data is written.                                                                        |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the register information.                                                                           |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| result:       | Contains the result of the synchronous write.                                                                |

---

`ModbusTCP.Master.WriteMultipleRegister(System.UInt16,System.Byte,System.UInt16,System.Byte[])`

Write multiple registers in slave asynchronous. The result is given in the response function.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address to where the data is written.                                                                        |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the register information.                                                                           |

---

`ModbusTCP.Master.WriteMultipleRegister(System.UInt16,System.Byte,System.UInt16,System.Byte[],System.Byte[])`

Write multiple registers in slave synchronous.

| Name          | Description                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| id:           | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| unit:         | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| startAddress: | Address to where the data is written.                                                                        |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| values:       | Contains the register information.                                                                           |
| Name          | Description                                                                                                  |
| -----         | ------                                                                                                       |
| result:       | Contains the result of the synchronous write.                                                                |

---

`ModbusTCP.Master.ReadWriteMultipleRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.UInt16,System.Byte[])`

Read/Write multiple registers in slave asynchronous. The result is given in the response function.

| Name               | Description                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| id:                | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| unit:              | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| startReadAddress:  | Address from where the data read begins.                                                                     |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| numInputs:         | Length of data.                                                                                              |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| startWriteAddress: | Address to where the data is written.                                                                        |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| values:            | Contains the register information.                                                                           |

---

`ModbusTCP.Master.ReadWriteMultipleRegister(System.UInt16,System.Byte,System.UInt16,System.UInt16,System.UInt16,System.Byte[],System.Byte[])`

Read/Write multiple registers in slave synchronous. The result is given in the response function.

| Name               | Description                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| id:                | Unique id that marks the transaction. In asynchonous mode this id is given to the callback function.         |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| unit:              | Unit identifier (previously slave address). In asynchonous mode this unit is given to the callback function. |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| startReadAddress:  | Address from where the data read begins.                                                                     |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| numInputs:         | Length of data.                                                                                              |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| startWriteAddress: | Address to where the data is written.                                                                        |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| values:            | Contains the register information.                                                                           |
| Name               | Description                                                                                                  |
| -----              | ------                                                                                                       |
| result:            | Contains the result of the synchronous command.                                                              |

---

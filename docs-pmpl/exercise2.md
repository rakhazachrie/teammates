# ISP Documentation for joinCourseForStudent

## Input Domain Model

| Characteristics  | b1            | b2            |
|------------------|---------------|---------------|
| registrationKey is String  |  True | False  |
| googleId is String  |  True | False  |
| Cari Student | Valid | Invalid Student |
| Create Student | Valid | Invalid |

Note :
* Fungsi joinCourseForStudent menerima 2 parameter yaitu String registrationKey dan String googleId
* Jika tipe parameter bukan tipe String akan throw InvalidParametersException
* Jika Student gagal ditemukan berdasarkan paramater, akan throw EntityDoesNotExistException
* Jika Student sudah dicreate, akan throw EntityAlreadyExistsException

## IDM Relabeling Table

| Characteristics | b1  | b2  |
|-----------------|-----|-----|
| A               | A1  | A2  |     
| B               | B1  | B2  |     
| C               | C1  | C2  |     
| D               | D1  | D2  |     
## Constraints


## Test Values and Example I/O

Criteria Used: All Combinations (ACoC)

| Test Value | Example Input | Expected Output |
|------------|---------------|-----------------|
| A1B1C1D1   | key1, id1     | Student1 berhasil terdaftar  |
| A1B1C1D2   | key2, id2     | Student2 berhasil terdaftar  |
| A1B1C2D1   | key1, id1     | Student1 berhasil terdaftar  |
| A1B1C2D2   | key1, id1     | EntityAlreadyExistsException |
| A2B1C1D1   | 2, id1        | InvalidParametersException   |
| A2B1C1D2   | 2, id1        | InvalidParametersException   |
| A2B1C2D1   | 2, id1        | InvalidParametersException   |
| A2B1C2D2   | 2, id1        | InvalidParametersException   |
| A1B2C1D1   | key1, 2       | InvalidParametersException   |
| A1B2C1D2   | key1, 2       | InvalidParametersException   |
| A1B2C2D1   | key1, 2       | InvalidParametersException   |
| A1B2C2D2   | key1, 2       | InvalidParametersException   |
| A2B2C1D1   | 1, 2          | InvalidParametersException   |
| A2B2C2D1   | 1, 2          | InvalidParametersException   |
| A2B2C1D2   | 1, 2          | InvalidParametersException   |
| A2B2C2D2   | 1, 2          | InvalidParametersException   |

Note: Pada test A1B1C1D1, A1B1C1D2, A1B1C2D1 dapat terjadi EntityDoesNotExistException
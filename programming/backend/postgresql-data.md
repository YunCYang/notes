# PostgreSQL

## System Columns

### ctid (and oid)
`ctid`: The physical location of the row version within its table. Can be used to locate the row version quickly. Note that a row's ctid will change if it is updated or moved by `VACUUM FULL`, therefore is useless as a long-term row identifier.

Example of using `ctid` - deleting limiting amount of duplicated data. `limit` cannot be use together with `delete` command.
```
DELETE FROM "logtable"
      WHERE "ctid" IN (
     SELECT "ctid"
       FROM "logtable"
   ORDER BY "timestamp"
      LIMIT 10
);
```

`oid` can also be used, but it only exists if you specifically ask for it when you create the table.
```
CREATE TABLE "type" (
	"typeId" serial NOT NULL,
	"typeName" varchar(255) NOT NULL,
	CONSTRAINT "type_pk" PRIMARY KEY ("typeId")
) WITH (
  OIDS=FALSE
);
```
`tableoid` is the oid of the table containing this row.

[Back](../../README.md)

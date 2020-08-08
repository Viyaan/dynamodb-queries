aws dynamodb list-tables 
aws dynamodb put-item --table-name Music --item file://song1.json
aws dynamodb put-item --table-name Music --item file://song2.json
aws dynamodb put-item --table-name Music --item file://song3.json
aws dynamodb query --table-name Music --key-condition-expression "Artist =:v1" --expression-attribute-values file://values1.json
aws dynamodb query --table-name Music --key-condition-expression "Artist =:v1 AND SongTitle = :v2" --expression-attribute-values file://values2.json
aws dynamodb delete-item --table-name Music --key file://keysToDelete.json
aws dynamodb scan --table-name Music

aws dynamodb query --table-name Music --key-condition-expression "Artist =:v1" --filter-expression "Released= :v2" --expression-attribute-values file://filterValues1.json


aws dynamodb scan --table-name Music --filter-expression "SongTitle= :v1" --expression-attribute-values file://filterValues2.json

aws dynamodb create-backup --table-name Music --backup-name MusicBackup


aws dynamodb describe-backup --backup-arn 

aws dynamodb restore-table-from-backup --target-table-name MusicRestored --backup-arn arn:aws:dynamodb:us-east-1:130738026255:table/Music/backup/01596630381253-81feb24d


aws dynamodb describe-table --table-name MusicRestored

aws dynamodb scan --table-name Music
aws dynamodb scan --table-name Music --max-items 3
aws dynamodb batch-write-item --request-items file://batchWrite.json
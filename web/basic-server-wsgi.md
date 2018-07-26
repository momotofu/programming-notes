import psycopg2

def connect():
	try:
		print('Connecting to the PostgreSQL database...')
		conn = psycopg2.connect("dbname=postgres user=postgres password=postgres")
		# create a cursor
		cur = conn.cursor()
		return conn, cur
	except (Exception, psycopg2.DatabaseError) as error:
		print('connection error: ', error)


def application(environ, start_response='test'):
	status = '200 OK'
	try:
		conn, cur = connect()
		cur.execute('select * from films;')
		films = cur.fetchone()
		cur.close()
		output = ''
		for attr in films:
			output += str(attr + ' ')

		response_headers = [('Content-type', 'text/plain'), ('Content-Length', str(len(output)))]
		if start_response is not 'test':
			start_response(status, response_headers)

		return [output]

	except (Exception) as error:
		print('Error: ', error)

if __name__ == '__main__':
	application('test')

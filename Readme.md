
https://blog.miniasp.com/post/2008/06/30/Using-ApacheBench-ab-to-to-Web-stress-test

public static DataTable GetDataTable(int dbindex, string sqlQuery)
{
	string connectionString = GetConnectionString(dbindex);
	using (SqlConnection sqlConnection = new SqlConnection(connectionString))
	{
		DataTable dataTable = new DataTable();
		sqlConnection.Open();
		SqlDataAdapter sqlDataAdapter = new SqlDataAdapter();
		SqlCommand sqlCommand = new SqlCommand(sqlQuery, sqlConnection);
		sqlCommand.CommandTimeout = CommandTimeout();
		sqlDataAdapter.SelectCommand = sqlCommand;
		sqlDataAdapter.Fill(dataTable);
		return dataTable;
	}
}

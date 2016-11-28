
<!doctype html>
<html lang="en">
<head>
	<!--<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">-->
	<meta charset="utf-8">
	<title>Agar.io clone roadmap </title>
</head>
<style>
	table {
		width: 100%;
		border: 1px solid black;
	}
	
	td,tr {
		border: 1px solid black;
	}
	
	.heading,th {
		width: 100%;
		color: white;
		background-color: #cd040b;
	}
	
	.header {
		background-color: mediumSlateBlue;
		font-weight: bolder;
		color: springGreen;
	}
	
	.cell {
		width: 100%;
	}
</style>
<body>
	<center>
		<h1>Agar.io Clone Roadmap </h1>
	</center>
	<table>
		<tr class="heading">
			<th>Features </th>
		</tr>
		<tr class="header">
			<b>
				<td>Assigned</li>
				<td>Name</td>
				<td>Description </td>
				<td>Status </td>
				<td>Percentage </td>
				<td>ToDo List </td>
			</b>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Skins </td>
			<td>Allow user to select a skin for thier cell </td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Allow player to spend premium currency on new skins</li>
					<li>Allow player to switch between skins </li>
				</ul>
			</td>
		</tr>
		<tr class="heading">
			<th>Server</th>
		</tr>
		<tr class="header">
			<b>
				<td>Assigned</li>
				<td>Name</td>
				<td>Description </td>
				<td>Status </td>
				<td>Percentage </td>
				<td>ToDo List </td>
			</b>
		</tr>
		<tr class="cell">
			<td>
				<li>FlamingGenius</li>
			</td>
			<td>Database</td>
			<td>Create tables and setup database for pooling users</td>
			<td>In Progress</td>
			<td>50%</td>
			<td>
				<ul>
					<li>Implement database connections </li>
					<li>Setup database tables </li>
					<li>Create user accounts and system </li>
					<li>Log incorrect passwords in database [admin]</li>
				</ul>
			</td>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Handling players</td>
			<td>Create a better connection between the server and client for better, smoother performance</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Possible add new framework</li>
				</ul>
			</td>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Performance Enhancement</td>
			<td>Handle user movement on client</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Move user on client</li>
					<li>Update player position on server</li>
				</ul>
			</td>
		</tr>
		<tr class="heading">
			<th>Mechanics</th>
		</tr>
		<tr class="header">
			<b>
				<td>Assigned</li>
				<td>Name</td>
				<td>Description </td>
				<td>Status </td>
				<td>Percentage </td>
				<td>ToDo List </td>
			</b>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Level/xp</td>
			<td>Integrate player leveling and xp system</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Player should gain levels based on xp</li>
					<li>Player level and xp should be stored and retrived from database </li>
					<li>Player starting mass should be incremented by 2 for each level from starting mass (level 1 = 10, level 2 = 12...)</li>
				</ul>
			</td>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Boost</td>
			<td>Implement boost into game</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Mass Boost (2x,3x,4x,5x)</li>
					<li>Xp Boost (2x,3x,4x,5x)</li>
				</ul>
			</td>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Store</td>
			<td>Setup store for spending premium currency</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Menu for spending on skins</li>
					<li>Menu for spending on boost (mass boost,xp boost)</li>
					<li>Menu to spend premium currency to gain level </li>
				</ul>
			</td>
		</tr>
		<tr class="heading">
			<th>Purchases</th>
		</tr>
		<tr class="header">
			<b>
				<td>Assigned</li>
				<td>Name</td>
				<td>Description </td>
				<td>Status </td>
				<td>Percentage </td>
				<td>ToDo List </td>
			</b>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Create IAP</td>
			<td>Setup Purchases</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Create IAP service for computer through paypal</li>
					<li>Create IAP service for android billing system (google wallet)</li>
					<li>Create IAP service for ios billing system (itunes)</li>
				</ul>
			</td>
		</tr>
		<tr class="cell">
			<td>
				<li></li>
			</td>
			<td>Premium Currency</td>
			<td>Create premium currency for buying premium content</td>
			<td>Not Implemented </td>
			<td>0% </td>
			<td>
				<ul>
					<li>Create coins,diamons,gems some type of premium currency</li>
					<li>Implement system for purchasing premium currency with IAP</li>
				</ul>
			</td>
		</tr>
	</table>
</body>
</html>






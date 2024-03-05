if (!window.dash_clientside) {
    window.dash_clientside = {}
}



// window.dash_clientside.clientside3 = {
//     update_table: function(clickdata, selecteddata, table_data, selectedrows, store) {
// 	/**
// 	 * Update selected rows in table when clicking or selecting in map
// 	 * chart
// 	 *
// 	 * Parameters
// 	 * ----------
// 	 *
// 	 * clickdata: object (dict)
// 	 *     clicked points
// 	 * selected: object (dict)
// 	 *     box-selected points
// 	 * table_data: list of dict
// 	 *     data of the table
// 	 * selectedrows: list of indices
// 	 *     list of selected countries to be updated
// 	 * store: list
// 	 *     store[1] is the list of countries to be used when initializing
// 	 *     the app
// 	 */
//     	if ((!selecteddata) && (!clickdata)) {
// 	    // this is only visited when initializing the app
// 	    // we use a pre-defined list of indices
// 	    return store[1];
//         }
// 	if (!selectedrows) {
// 	    selectedrows = [];
// 	}
// 	var ids = [...selectedrows];

// 	var countries = [];
// 	if (clickdata) {
// 	    var country = clickdata['points'][0]['customdata'][0];
// 	    countries.push(country);
// 	}
// 	if (selecteddata) {
// 	    var countries = [];
// 		for (i = 0; i < selecteddata['points'].length; i++) {
// 		    countries.push(selecteddata['points'][i]['customdata'][0]);
// 	    }
// 	}
// 	for (i = 0; i < countries.length; i++) {
// 	    for (j = 0; j < table_data.length; j++) {
// 		if (countries[i] == table_data[j]["country_region"]) {
// 		    if (selectedrows.includes(j)){
// 			var index = ids.indexOf(j);
// 			ids.splice(index, 1);
// 			}
// 		    else{
// 			ids.push(j);
// 		    }
// 		}
// 	    }
// 	}
// 	return ids;
//     }
// };

    
window.dash_clientside.clientside = {
    update_graph: function(hoverdata, store) {
	/**
	 * Update figure
	 */
	// console.log(hoverdata);
	var datasetname = hoverdata['points'][0]['customdata'];
	// console.log(datasetname);
	

	var fig = store[0];
	var alldatasets = fig['data'][0]['customdata'];
	var idx_hover_dataset = alldatasets.indexOf(datasetname);
	// console.log(idx_hover_dataset);
	// console.log(fig);
	
	var new_fig = {};
	new_fig['data'] = fig['data'];
	new_fig['layout'] = fig['layout'];
	for (i = 0; i < fig['layout']['shapes'].length; i++) {
	    new_fig['layout']['shapes'][i]["line"]["color"] = "gray";
	}
	new_fig['layout']['shapes'][idx_hover_dataset]["line"]["color"] = "red";

        return new_fig;
    }
};

    
window.dash_clientside.clientside2 = {
    update_info: function(hoverdata, store) {
	/**
	 * Update figure
	 */
	// console.log(hoverdata);
	var datasetname = hoverdata['points'][0]['customdata'];
	console.log(datasetname);
	

	var fig = store[0];
	var data = store[1];
	var alldatasets = fig['data'][0]['customdata'];
	var idx_hover_dataset = alldatasets.indexOf(datasetname);
	console.log(idx_hover_dataset);
	console.log(fig);
	console.log(data[idx_hover_dataset]);
	var link = data[idx_hover_dataset]['hf_link'];
	var num_samples = data[idx_hover_dataset]['num_samples'];
	
	return [
		{
			type: "H6", 
			namespace: "dash_html_components",
			props: {children: datasetname},
		},
		{
			type: "A", 
			namespace: "dash_html_components",
			props: {children: "Link to dataset", href:link},
		},
		{
			type: "P", 
			namespace: "dash_html_components",
			props: {children: "Train set size: " + num_samples},
		},
	];
    }
};


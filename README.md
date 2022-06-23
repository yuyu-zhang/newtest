# newtest
static DISTANCE: f64 = 1.0; //the width we want to enlarge (global static variable)
static AOW:u32 = 3;       // the number of the arrow between two nearby points


fn handle(arr: &mut Vec<f64>) -> Vec<f64> { // handle the vector in order to cut off the former two. // it was used to add return type.
    let mut hdv:Vec<f64> = Vec::new(); //
    let mut hdv1:Vec<f64> = Vec::new();
    for i in 2..arr.len(){
        hdv.push(arr[i]);


    }


    println!("{:?} data cut is:",hdv);


    hdv

}

fn handle1(arr: &Vec<f64>) -> Vec<f64> { // handle the vector in order to cut off the former two. // it was used to add return type.

    let mut hdv1:Vec<f64> = Vec::new();

    for i in 0..2{
        hdv1.push(arr[i]);
    }
    println!("{:?} data cut is:",hdv1);


    hdv1

}



// fn broader(arr: Vec<f64>)  -> Vec<f64>{ // return the road which are broder
//
// }


fn vertical(mut arr: &mut Vec<f64>) -> Vec<f64>{
    let mut arf = Vec::new(); // void an empty matrix of the road (array after) remember: in order
    // let arf1 = arr;
    // let xx = handle(arr);
    // let mut xy =xx[2];

    //println!("{}",xy);
    let arr1 =handle(&mut arr); //
    let arr2 = handle1(&mut arr); // passing value

    arf.push(0.2784); // RBG color index, which is fixed
    arf.push(0.2784);
    arf.push(0.2784);

    for i in (0..arr1.len()-1).filter(|x| x % 4 == 0) { // xl yl xl1 yl1 xr1 yr1  xr yr

        // xl = aro[i] - DISTANCE;
        // yl = aro[i + 1];
        // xl1 = aro[i + 2] - DISTANCE;
        // yl1 = aro[i + 3];
        //
        // xr1 = aro[i + 2] + DISTANCE;
        // yr1 = aro[i + 3];
        // xr = aro[i] + DISTANCE;
        // yr = aro[i + 1];


        arf.push(arr1[i] - DISTANCE);
        arf.push(arr1[i + 1] ); // add the new coordinate into the matrix
        arf.push(0.009999999776482582);// all of the rest are fixed number
        arf.push(0.0);
        arf.push(0.0);
        arf.push(1.0);
        arf.push(0.3411764705882353);
        arf.push(0.5058823529411764);
        arf.push(1.0);
        arf.push(arr2[1]);

        arf.push(arr1[i + 2] - DISTANCE);
        arf.push(arr1[i + 3] ); // add the new coordinate into the matrix
        arf.push(0.009999999776482582);// all of the rest are fixed number
        arf.push(0.0);
        arf.push(0.0);
        arf.push(1.0);
        arf.push(0.3411764705882353);
        arf.push(0.5058823529411764);
        arf.push(1.0);
        arf.push(arr2[1]);

        arf.push(arr1[i + 2] + DISTANCE);
        arf.push(arr1[i + 3] ); // add the new coordinate into the matrix
        arf.push(0.009999999776482582);// all of the rest are fixed number
        arf.push(0.0);
        arf.push(0.0);
        arf.push(1.0);
        arf.push(0.3411764705882353);
        arf.push(0.5058823529411764);
        arf.push(1.0);
        arf.push(arr2[1]);

        arf.push(arr1[i] + DISTANCE);
        arf.push(arr1[i + 1]); // add the new coordinate into the matrix
        arf.push(0.009999999776482582);// all of the rest are fixed number
        arf.push(0.0);
        arf.push(0.0);
        arf.push(1.0);
        arf.push(0.3411764705882353);
        arf.push(0.5058823529411764);
        arf.push(1.0);
        arf.push(arr2[1]);
    }
    println!("{:?}",arf);
    arf

}

// fn horizontal(arr: Vec<f64>)  -> Vec<f64>{ // if it is horizontal: we should do it later.
//
//
// }

//
// fn Rcorner(arr: Vec<usize>)  -> Vec<usize>{ //realise the angle to be smooth: to be continued.
//     x=1;
//
// }

// fn anglejug(arr: Vec<f64>)  -> Vec<f64>{ // no need to specific what the number , we should alter it later
//     let mut angle:Vec<f64> = Vec::new();
//     for i in (0..arr.len()-2).filter(|x| x&2 == 0){
//         angle.push(i)
//
//     }
//     angle
//
// }
//
fn Index(mut arr: &mut Vec<f64>) { // that is the method of derive the index of the two points.

    let mut ind = Vec::new();

    let arr1 =handle(&mut arr); // calling back

    let mut len= arr1.len();

    let mut count = (len / 2) *2 -1 ;

    for i in 0..=count{
        i as i32;
        ind.push(i);

    }
    let mut ind1 = Vec::new();
    for i in (0..ind.len()).filter(|x| x % 4 == 0) {
        ind1.push(ind[i + 3]);
        ind1.push(ind[i + 1]);
        ind1.push(ind[i]);
        ind1.push(ind[i + 1]);
        ind1.push(ind[i + 3]);
        ind1.push(ind[i + 2]);
    } // modify it such that it become the ordered vector with length of the count
    print!("{:?}",ind);
    print!("{:?}", ind1)


}
//
// fn Acquire(arr: Vec<usize>)  -> Vec<usize> { // obtain the distance between the road.
//
//
// }

fn arrow(mut arr: &mut Vec<f64>)  -> Vec<f64>{ // return three arrow between two road

    let mut gui =   Vec::new();
    let mut arr2 =   Vec::new();
    let arr3 = handle1(&mut arr); // passing value
    let arr1 =vertical(&mut arr); // passing the handled array
    for i in 3..arr1.len(){
        arr2.push(arr1[i]);

    }


    let mut row = arr[5] - arr[3]; // add the distance between two points
    let mut interval = (row - 3.0 * DISTANCE) / 4.0;

    for i in(0..arr2.len()).filter(|x| x % 40 == 0) {  // index start

        for j in 0..3 { //each 4 points has 4 arrow points.
            gui.push(arr2[i + 30]);
            gui.push(arr2[i + 1] + (j +1) as f64 * interval + 2.0 * (j) as f64 * DISTANCE); //because it is double distance
            gui.push(0.009999999776482582);
            gui.push(0.0);
            gui.push(1.0);
            gui.push(arr3[1]);


            gui.push(arr2[i + 30]);
            gui.push(arr2[i + 1] + (j +1) as f64 * interval + 2.0 * (j + 1) as f64 * DISTANCE);
            gui.push(0.009999999776482582);
            gui.push(0.0);
            gui.push(0.0);
            gui.push(arr3[1]);

            gui.push(arr2[i]);
            gui.push(arr2[i + 1] +(j +1) as f64 *  interval + 2.0 * (j + 1) as f64 * DISTANCE);
            gui.push(0.009999999776482582);
            gui.push(1.0);
            gui.push(0.0);
            gui.push(arr3[1]);

            gui.push(arr2[i]);
            gui.push(arr2[i + 1] + (j +1) as f64 * interval + j as f64 * 2.0 * DISTANCE);
            gui.push(0.009999999776482582);
            gui.push(1.0);
            gui.push(1.0);
            gui.push(arr3[1]);
        }
    }
    print!("Inside update {:?}",gui);
    println!("{}hhhhh",interval);
    println!("{}hhh",row);
    gui


}

fn IndexA(mut arr: &mut Vec<f64>) { // that is the method of derive the index of the arrow

    let mut inda = Vec::new();

    let arr1 = arrow(&mut arr); // calling back

    let mut len= arr1.len();

    let mut count = (len / 6) -1 ;

    for i in 0..=count{
        i as i32;
        inda.push(i);

    }
    let mut inda1 = Vec::new();
    for i in (0..inda.len()).filter(|x| x % 4 == 0) {
        inda1.push(inda[i + 3]);
        inda1.push(inda[i ]);
        inda1.push(inda[i + 2]);
        inda1.push(inda[i + 2]);
        inda1.push(inda[i ]);
        inda1.push(inda[i + 1]);
    } // modify it such that it become the ordered vector with length of the count
    print!("{:?}",inda);
    print!("{:?}", inda1)


}









fn main() {
    let mut ro = vec![1.0, 9.970000267028809, 90.383056640625, 7.470924377441406,
                      90.383056640625, 30.45943260192871]; //make a test of the internal array.

    handle (&mut ro); //hdv()
    vertical(&mut ro);
    Index(&mut ro);
    arrow(&mut ro);
    IndexA(&mut ro);





    //vertical(hdv);
    // broader();
    // arrow();
    // Index();

}


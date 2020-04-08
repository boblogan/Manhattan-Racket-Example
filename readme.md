# Manhattan alghoritm (3D)

Imagine seeking a path from a given source to given destination in a Manhattan-like city grid.
How many path there are to arrive to point a to point b?

This variant assumes that that the grid is a 3D space

ANSWER:

(define manhattan-3d                       
  (lambda (i j k)
    (cond
      ((and (= j 0) (= k 0)) 1)
      ((and (= j 0) (= i 0)) 1)
      ((and (= k 0) (= i 0)) 1)   
      ((= i 0) (+  (manhattan-3d i (- j 1) k)
                   (manhattan-3d i j (- k 1))))
      ((= k 0) (+  (manhattan-3d i (- j 1) k)
                   (manhattan-3d (- i 1) j k)))
      ((= j 0) (+  (manhattan-3d i j (- k 1))
                   (manhattan-3d (- i 1) j k)))
      (else
       (+  (manhattan-3d i (- j 1) k)
           (manhattan-3d (- i 1) j k)
           (manhattan-3d i j (- k 1))))
      )
    )
  )

(manhattan-3d 0 0 7) ;1
(manhattan-3d 2 0 2) ;6
(manhattan-3d 1 1 1) ;6
(manhattan-3d 1 1 5) ;42
(manhattan-3d 2 3 1) ;60
(manhattan-3d 2 3 3) ;560